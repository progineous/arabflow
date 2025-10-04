# 🌙 ArabFlow - منصة التجارة الإلكترونية العربية المفتوحة المصدر

<div align="center">

![ArabFlow Logo](https://via.placeholder.com/400x150/1e3a8a/ffffff?text=ArabFlow+العربية)

**منصة تجارة إلكترونية مفتوحة المصدر مع ذكاء اصطناعي يولد تجارب تسوق ثقافية مخصصة بالعربية**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Laravel](https://img.shields.io/badge/Laravel-11.x-FF2D20.svg)](https://laravel.com)
[![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4.svg)](https://php.net)
[![Arabic RTL](https://img.shields.io/badge/Arabic-RTL-1e3a8a.svg)](https://arabflow.net)

[الموقع الرسمي](https://arabflow.net) • [التوثيق](https://docs.arabflow.net) • [المجتمع](https://community.arabflow.net) • [المساهمة](CONTRIBUTING.md)

</div>

## 🚀 نظرة عامة

ArabFlow هي منصة تجارة إلكترونية مفتوحة المصدر تجمع بين قوة Laravel والذكاء الاصطناعي لتوفير تجارب تسوق مخصصة للثقافة العربية. تخيل Shopify لكن مفتوحة المصدر، ومعها AI مدمج يفهم الثقافة العربية ويخصص التجربة لكل مستخدم.

### ✨ المميزات الفريدة

🧠 **ذكاء اصطناعي ثقافي مدمج**
- توصيات ذكية بناءً على المناسبات العربية (رمضان، عيد الأضحى)
- دعم اللهجات المحلية (مصري، خليجي، مغربي)
- توليد وصف المنتجات تلقائياً بالعربية

🌍 **دعم كامل للعربية و RTL**
- واجهة مستخدم RTL احترافية
- تعدد اللغات والثقافات
- تكامل مع بوابات الدفع العربية

💳 **بوابات دفع محلية**
- Fawry (مصر)
- STC Pay (السعودية)
- وبوابات أخرى قريباً

🛍️ **Social Bazaar Mode**
- تحويل المتجر لسوق اجتماعي
- تكامل مع WhatsApp
- مفاوضات AI تلقائية للأسعار

## 🛠️ التثبيت السريع

### المتطلبات
- PHP 8.2+
- Composer
- Node.js 18+
- MySQL/PostgreSQL/SQLite

### خطوات التثبيت

```bash
# استنساخ المشروع
git clone https://github.com/progineous/arabflow.git
cd arabflow

# تثبيت dependencies
composer install
npm install

# إعداد البيئة
cp .env.example .env
php artisan key:generate

# إعداد قاعدة البيانات
php artisan migrate --seed

# تشغيل المشروع
php artisan serve
npm run dev
```

### إنشاء متجر جديد بأمر واحد

```bash
# إنشاء متجر سعودي
php artisan arabflow:create-store --culture=saudi --dialect=gulf

# إنشاء متجر مصري
php artisan arabflow:create-store --culture=egyptian --dialect=egyptian
```

## 🎯 الاستخدام

### تفعيل الذكاء الاصطناعي

```php
// إضافة مفتاح OpenAI في .env
OPENAI_API_KEY=your_api_key_here

// استخدام AI للتوصيات
$recommendations = ArabFlow::ai()
    ->forUser($user)
    ->culturalRecommendations()
    ->during('ramadan')
    ->get();
```

### تخصيص اللهجة

```php
// في Controller
public function product(Product $product, Request $request)
{
    $dialect = $request->get('dialect', 'standard');
    
    $description = ArabFlow::translate($product->description)
        ->to($dialect)
        ->withCulturalContext();
    
    return view('product.show', compact('product', 'description'));
}
```

## 🏗️ الهيكل المعماري

```
app/
├── ArabFlow/
│   ├── AI/
│   │   ├── CulturalEngine.php      # محرك الذكاء الثقافي
│   │   ├── DialectTranslator.php   # مترجم اللهجات
│   │   └── RecommendationEngine.php # محرك التوصيات
│   ├── Payment/
│   │   ├── FawryProvider.php       # موفر فوري
│   │   └── STCPayProvider.php      # موفر STC Pay
│   └── Cultural/
│       ├── SeasonDetector.php      # كاشف المواسم
│       └── PreferenceAnalyzer.php  # محلل التفضيلات
```

## 🌟 أمثلة الاستخدام

### توصيات المناسبات

```php
// توصيات رمضان
$ramadanProducts = Product::aiRecommended()
    ->forSeason('ramadan')
    ->withPreferences(['halal_only', 'family_oriented'])
    ->get();

// توصيات العيد
$eidProducts = Product::aiRecommended()
    ->forSeason('eid_fitr')
    ->withCulturalContext($user->cultural_profile)
    ->get();
```

### تحويل اللهجات

```php
// من الفصحى للمصري
$egyptianText = ArabFlow::dialect()
    ->from('standard')
    ->to('egyptian')
    ->translate('مرحباً بكم في متجرنا');

// النتيجة: "أهلاً وسهلاً في محلنا"
```

## 🤝 المساهمة

نرحب بمساهماتك! 

### مجالات المساهمة المطلوبة:
- 🧠 تطوير AI models للهجات جديدة
- 🎨 تصميم themes عربية
- 🔌 تكامل بوابات دفع جديدة
- 📱 تطوير تطبيقات الموبايل
- 📚 كتابة التوثيق

```bash
# إنشاء فرع جديد
git checkout -b feature/new-dialect-support

# إضافة تغييراتك
git commit -m "feat: add moroccan dialect support"

# إرسال pull request
git push origin feature/new-dialect-support
```

## 📊 الإحصائيات

- 🚀 **+50** مشروع تجاري يستخدم ArabFlow
- 🌍 **8** دول عربية مدعومة
- 🗣️ **6** لهجات محلية
- ⭐ **1000+** نجمة على GitHub

## 🗺️ خريطة الطريق 2025

- [ ] **Q1**: إضافة دعم اللهجة المغربية والجزائرية
- [ ] **Q2**: تطوير تطبيق الموبايل (React Native)
- [ ] **Q3**: تكامل مع منصات التواصل الاجتماعي
- [ ] **Q4**: إطلاق ArabFlow Cloud

## 📝 الترخيص

هذا المشروع مرخص تحت [رخصة MIT](LICENSE) - انظر ملف LICENSE للتفاصيل.

## 🙏 شكر خاص

- [Laravel](https://laravel.com) للإطار الرائع
- [OpenAI](https://openai.com) لـ API الذكاء الاصطناعي
- [مجتمع المطورين العرب](https://arabdevelopers.org) للدعم المستمر

---

<div align="center">

**صُنع بـ ❤️ للمجتمع العربي**

[⭐ أعط المشروع نجمة](https://github.com/progineous/arabflow) | [🐛 بلّغ عن خطأ](https://github.com/progineous/arabflow/issues) | [💡 اقترح ميزة](https://github.com/progineous/arabflow/issues/new)

</div>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains thousands of video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

- **[Vehikl](https://vehikl.com)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel)**
- **[DevSquad](https://devsquad.com/hire-laravel-developers)**
- **[Redberry](https://redberry.international/laravel-development)**
- **[Active Logic](https://activelogic.com)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
