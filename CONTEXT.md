# NIX Agency — Контекст верстки

## Проект
Лендинг для digital-агентства NIX Agency. Чистый HTML + CSS (без фреймворков).
Макет: [Figma](https://www.figma.com/design/T3I2ue87iJuSS0jidd7txq/Landing-%E2%80%A2-NIX-Agency?node-id=20005072-2543&m=dev)

## Стек
- HTML5, CSS3 (custom properties, BEM)
- Шрифты: Onest (300/400/500), Unbounded (200/400/500) через Google Fonts
- Адаптив: **пока только 1200px десктоп**, мобильные адаптивы будут позже

## Структура файлов
```
index.html               — единственная страница
css/design-system.css     — токены (цвета, типографика, кнопки, reset)
css/main.css              — стили страницы
assets/logo.svg           — логотип NIX
assets/digital.png        — бейдж "DIGITAL • AGENCY •" (вращается)
assets/bitrix24.png       — логотип Bitrix24 (бейдж партнёра)
assets/icons/
  sparkle.svg             — звезда-sparkle (✦) рядом с заголовком hero
  star.svg                — декоративная звезда в фиолетовой карточке hero
  star-why.svg            — декоративная звезда в секции "Почему"
  star-services.svg       — декоративная звезда в секции "Услуги"
  sort.svg                — иконка sort (облако тегов)
  sort-card.svg           — иконка sort (карточка "Почему", оранж кружок)
  flame.svg               — иконка пламени (карточка "Почему", розов кружок)
  share.svg               — иконка share (карточка "Почему", фиолет кружок)
  code.svg                — иконка </> (карточка "Дизайн и разработка")
  clock.svg               — иконка часов (карточка "Внедрение Битрикс24")
  telegram.svg            — иконка Telegram
  whatsapp.svg            — иконка WhatsApp
  arrow-up-right.svg      — стрелка
  marquee-star.svg        — звезда для бегущей строки
  folder.svg              — иконка папки
  tilda.svg               — логотип Тильды (бейдж в кейсах)
```

## Цветовые токены
| Токен | Hex | Использование |
|-------|-----|---------------|
| cocane | #FFFFFF | белый фон, текст кнопок, фон карточек "Почему" |
| neutral | #F5F5F5 | фон body |
| dark | #121313 | текст, кнопки |
| violet | #D7D6FF | hero карточка, @ кружок, иконка share, карточка услуг |
| lime | #CCFF7A | hero карточка услуг, карточка услуг |
| orange | #F9CD67 | иконка sort в секции "Почему" |
| pink | #FEBEE7 | иконка flame в секции "Почему" |
| grey | #8F8F9C | нумерация карточек (01, 02, 03) |
| 4-stars | #BDBCE0 | декоративные звёзды |

## Сверстанные секции

### 1. Header (Figma node 20005072:2613)
- Логотип слева, навбар по центру (backdrop-blur, белый bg, rounded), CTA "связаться" справа

### 2. Hero (Figma node 20005072:2543)
- Заголовок: "ЦИФРОВЫЕ РЕШЕНИЯ" (Unbounded Medium 42px) + "для вашего бизнеса" (Unbounded 200 44px)
- Sparkle, вращающийся бейдж "DIGITAL • AGENCY •"
- Фиолетовая карточка (614×280px): текст, кнопка "обсудить проект", соцсети
- Лаймовая карточка (flex:1, 280px): "Смотреть услуги" + облако тегов (абсолютное позиционирование, повороты)

### 3. Бегущая строка (Figma node 20005072:2633)
- Тёмная полоса, "DIGITAL AGENCY ✦" с бесконечной прокруткой

### 4. Секция "Почему проекты с нами успешнее" (Figma node 20005072:2641)
- Заголовок: Unbounded Medium 32px uppercase
- Декоративная звезда справа вверху
- 3 белые карточки (`article.why__card`, flex, gap 8px, h: 380px, radius 24px):
  - 01 — оранжевый кружок (sort, rotate 90°), «Погружаемся в ваш продукт»
  - 02 — розовый кружок (flame), «Опыт и сильная команда»
  - 03 — фиолетовый кружок (share), «Битрикс24 и бизнес-экспертиза»
- **Hover-анимация карточек** (Figma node 20005119:68627):
  - При наведении выезжает разделитель + описание (`.why__card-reveal`)
  - Реализовано через CSS Grid `grid-template-rows: 0fr → 1fr`
  - Структура: `.why__card-body` (margin-top:auto) > номер + h3-заголовок + `.why__card-reveal` > `.why__card-reveal-inner` > hr + p

### 5. Секция "Услуги" (Figma node 20005072:2668)
- Заголовок: Unbounded Medium 32px uppercase + декоративная звезда (абсолютно спозиционирована: 20px вправо и 20px вверх от h2)
- 2 карточки (flex:1, h:500px, gap:8px, radius:24px):
  - Лайм (#CCFF7A): "Дизайн и разработка сайтов", иконка code вверху справа, цена "от 60 000 ₽" внизу
  - Фиолет (#D7D6FF): "Внедрение Битрикс24", иконка clock вверху справа, цена "от 50 000 ₽" внизу, бейдж "Мы — официальный партнёр Bitrix24"
- **Hover**: лайм → #B9FF49, фиолет → #C7C6FF, transition 0.3s

## Порядок секций в HTML
1. Header
2. Hero
3. Marquee (бегущая строка)
4. Why Us
5. Services (Услуги)
6. Cases (Кейсы)

## Сверстанные секции (продолжение)

### 6. Секция "Кейсы" (Figma node 20005072:2733)
- Заголовок: "Кейсы" (Unbounded Medium 32px uppercase)
- Табы фильтрации: "все", "коммерческие сайты", "интернет-магазины" (pill-кнопки, active = тёмный фон)
- Ссылка "смотреть все" справа (Unbounded Medium 10px uppercase + стрелка)
- 4 карточки в `.cases__list` (flex column, gap 40px):
  - Каждая карточка (`article.cases__card`) = горизонтальный ряд: превью (670×500px, radius 24px) + инфо (flex:1)
  - **Чётные карточки** (2, 4): класс `.cases__card--reverse` → `flex-direction: row-reverse` (текст слева, превью справа)
  - Бейдж технологии (белый pill, абсолютно в правом нижнем углу превью): иконка + текст (напр. "Тильда")
  - Инфо: название проекта (Onest Medium 26px), URL (Unbounded Medium 13px, grey), кнопка "о проекте" (outline pill)
- **Кейс 1** — Lingo Magic, фиолетовый фон (`--violet`), бейдж Тильда, `lingo-magic.com`
- **Кейс 2** — Кампус, розовый фон (`--pink`), бейдж Тильда, reversed layout, `campus-courses.ru`
- **Кейс 3** — ALTTAB Game store, нейтральный фон (`--neutral`), `altar-game.ru`
- **Кейс 4** — Сайт для языковой школы, фиолетовый фон (`--violet`), `lang-school.ru`
- JS: фильтрация карточек по `data-category` при клике на табы

## Навигация (единая на всех страницах)

### Header (десктоп + мобильное меню)
| Пункт | Ссылка (index.html) | Ссылка (остальные) |
|-------|--------------------|--------------------|
| Главная | `/` | `/` |
| Услуги | `#services` | `/#services` |
| Кейсы | `/cases` | `/cases` |
| Блог | `/blog` | `/blog` |
| Контакты | `/contacts` | `/contacts` |

### Footer
| Элемент | Ссылка |
|---------|--------|
| Логотип | `/` |
| Услуги | `#services` (index) / `/#services` (остальные) |
| Кейсы | `/cases` |
| Блог | `/blog` |
| Контакты | `/contacts` |
| Дизайн и разработка сайтов | `/design` |
| Внедрение Битрикс24 | `/bitrix24` |
| Телефон | `tel:+79933091207` — +7 (993) 309-12-07 |
| Email | `mailto:info@nixagency.ru` — info@nixagency.ru |
| Telegram | https://t.me/nix_agency |
| WhatsApp | https://wa.me/79933091207?text= |

### Контакты в мобильном меню — те же данные (телефон, email, Telegram, WhatsApp)

### Страница /contacts — ещё не создана

## Что ещё НЕ сверстано
- Мокап-изображения внутри карточек кейсов (пока placeholder)
- Секция "Контакты" (#contacts)
- Страница /contacts
- Мобильные адаптивы

## Figma ключи
- fileKey: `T3I2ue87iJuSS0jidd7txq`
- Header: `20005072:2613`
- Hero section: `20005072:2543`
- Marquee: `20005072:2633`
- Why section (default): `20005072:2641`
- Why section (hover/animate): `20005119:68627`
- Services: `20005072:2668`
- Cases: `20005072:2733`
- Case 2 (Кампус): `20005105:22614`

## Семантика
- Заголовок секции — `h2`
- Заголовки карточек — `h3`
- Карточки "Почему" обёрнуты в `article`
- Карточки "Кейсы" обёрнуты в `article`

## Паттерны и решения
- Контейнер: `.page` max-width 1440px, `.container` max-width 1200px, padding 0 60px
- Анимации reveal: CSS Grid `grid-template-rows: 0fr → 1fr` (секция Why)
- Бегущая строка: дублированный `.marquee__content`, `translateX(-50%)` бесконечный цикл
- Вращающийся бейдж: `@keyframes spin` 25s linear infinite, класс `.rotating-badge`
- Облако тегов (hero): абсолютное позиционирование каждого тега с индивидуальным `rotate()`
- Декоративные звёзды: inline SVG с `#BDBCE0`, абсолютное позиционирование
- Зеркальная раскладка кейсов: `.cases__card--reverse` с `flex-direction: row-reverse`
