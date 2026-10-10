# GymFit — سورس اپلیکیشن Flutter

اپلیکیشن فارسی و راست‌چین مدیریت تمرین باشگاه. داده‌ها به‌صورت محلی در SQLite دستگاه نگهداری می‌شوند.

## وضعیت تحویل
- سورس کامل پروژه Flutter و پیکربندی Android در این بسته موجود است.
- در محیط ساخت فعلی Flutter، Dart، Java/JDK و Android SDK نصب نیستند؛ بنابراین APK از اینجا ساخته نشده است.
- برای ساخت Android، فایل‌های Gradle Wrapper تولیدشده (`gradlew` و پوشه `gradle/wrapper`) ممکن است لازم باشند و در این بسته به‌عنوان فایل‌های تولیدی وجود ندارند. دستور `flutter create --platforms=android .` در راهنما و workflow برای آماده‌سازی آن‌هاست.
- نسخهٔ APK را پس از build از مسیر `build/app/outputs/flutter-apk/app-release.apk` دریافت کنید.

## ساخت APK در یک اجرای GitHub Actions (پیشنهادی)
1. محتوای ZIP را در یک مخزن GitHub بارگذاری/commit کنید.
2. در GitHub به تب **Actions** بروید و workflow **Build Android APK** را انتخاب کنید.
3. روی **Run workflow** بزنید. (همچنین با push به شاخهٔ `main` یا `master` اجرا می‌شود.)
4. پس از اتمام موفق، صفحهٔ اجرای workflow را باز کرده و از بخش **Artifacts** فایل `gymfit-release-apk` را دانلود کنید؛ APK درون آن است.

قالب workflow در `.github/workflows/build-apk.yml` موجود است. GitHub Actions به اینترنت دسترسی دارد و Flutter/Android SDK/JDK را در runner نصب/آماده می‌کند؛ این مراحل در سندباکس آفلاین حاضر قابل انجام نبود.

## ساخت محلی با Flutter یا Android Studio
پیش‌نیاز: Flutter پایدار (Dart 3.3 یا جدیدتر)، Android SDK و JDK 17.

در ترمینال، از ریشهٔ پروژه اجرا کنید:
```bash
flutter create --platforms=android .
flutter pub get
flutter build apk --release
```

خروجی: `build/app/outputs/flutter-apk/app-release.apk`. برای APK آزمایشی می‌توان از `flutter build apk --debug` استفاده کرد. در Android Studio، پوشهٔ پروژه را باز کنید، Flutter SDK را معرفی و Android SDK را نصب/پیکربندی کنید؛ سپس همین دستورات را از ترمینال IDE اجرا کنید.

## امکانات اپلیکیشن
- داشبورد، برنامهٔ تمرینی سه‌روزه و بانک ۱۰ حرکت
- ثبت ست، تکرار، وزنه و سوابق تمرین
- ثبت وزن، نمودار روند و محاسبهٔ BMI
- پروفایل نمونه، رابط تیره و فارسی RTL
- بدون نیاز به حساب کاربری؛ داده‌های نمونه هنگام نخستین اجرا ایجاد می‌شوند.
