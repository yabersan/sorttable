# 📡 Route Table Viewer

Приложение на React + TypeScript, отображающее таблицу маршрутов IPv4 с возможностью сортировки. Данные загружаются из локального JSON-файла (`/data.json`), а таблица поддерживает сортировку по адресу, шлюзу и интерфейсу.

## 🚀 Технологии

-   [React 19](https://react.dev/)
-   [Vite](https://vitejs.dev/)
-   [TypeScript](https://www.typescriptlang.org/)
-   CSS (ручная стилизация)
-   Fetch API

## 📦 Установка и запуск

1. **Клонируйте репозиторий:**

```bash
git clone https://github.com/yabersan/sorttable.git
cd sorttable
```

2. **Установите зависимости:**

```bash
npm install
```

3. **Запустите проект в режиме разработки:**

```bash
npm run dev
```

Откройте в браузере [http://localhost:5173](http://localhost:5173)

## 🗂 Структура проекта

```
.
├── public/
│   └── data.json            # Локальный JSON с маршрутами
├── src/
│   ├── components/
│   │   └── Table.tsx        # Таблица маршрутов
│   ├── styles/
│   │   └── Table.css        # Стилизация таблицы
│   ├── types/
│   │   └── index.ts         # Интерфейс Route
│   ├── App.tsx              # Главный компонент
│   ├── App.css              # Глобальные стили
│   └── main.tsx             # Точка входа
├── package.json
├── tsconfig.json
└── README.md
```

## 📊 Описание функциональности

-   📥 Загрузка маршрутов из `data.json`
-   🔃 Сортировка таблицы по трем полям: `Адрес назначения`, `Шлюз`, `Интерфейс`
-   📌 Сортировка по IP-адресам производится по их числовому значению
-   ⚠️ Обработка ошибок загрузки данных
-   ⏳ Показ состояния загрузки

## 📘 Типы данных

```ts
// src/types/index.ts
export interface Route {
    uuid: string;
    address: string;
    mask: string;
    gateway: string;
    interface: string;
}
```

## 📄 Пример данных

Файл `public/data.json` содержит:

```json
{
    "routes": [
        {
            "uuid": "1",
            "address": "0.0.0.0",
            "mask": "/0",
            "gateway": "193.0.174.1",
            "interface": "Подключение Ethernet"
        },
        {
            "uuid": "2",
            "address": "10.1.30.0",
            "mask": "/24",
            "gateway": "0.0.0.0",
            "interface": "Гостевая сеть"
        }
    ]
}
```

## 🧠 Как работает сортировка

Сортировка происходит при клике на заголовок столбца. Для IP-адресов (`address`, `gateway`) применяется функция `ipToNumber`, чтобы обеспечить корректную сортировку по числовому значению.

CSS-классы `.sorted-asc` и `.sorted-desc` добавляют стрелки рядом с активным заголовком таблицы.

## 💡 Особенности

-   Работает без внешнего API — данные хранятся локально.
-   Использует `useEffect` и `useState` для загрузки и отображения данных.
-   Код написан с использованием строгой типизации через TypeScript.

## ⚙️ Скрипты

| Скрипт            | Назначение                      |
| ----------------- | ------------------------------- |
| `npm run dev`     | Запуск dev-сервера              |
| `npm run build`   | Сборка production-версии        |
| `npm run preview` | Предпросмотр собранного проекта |
| `npm run lint`    | Проверка кода линтером          |


