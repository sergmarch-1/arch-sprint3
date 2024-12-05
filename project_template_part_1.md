Задание 1. Анализ и планирование
Чтобы составить документ с описанием текущей архитектуры приложения, можно часть информации взять из описания компании условия задания. Это нормально.

1. Описание функциональности монолитного приложения
**Управление отоплением:**

- Пользователи могут управлять отоплением в доме: приложение позволяет просматривать текущую температуру и задавать целевую, а также отключать\включать систему отопления.

**Мониторинг температуры:**

- Пользователи могут проверять текущую температуру с датчика. 
- Система считывает данные с датчика и сохраняет время последнего показания. 

2. Анализ архитектуры монолитного приложения
- монолитное приложение на Java с СУБД Postgres
- БД содержит две таблицы: heating_systems и temperature_sensors, данные в которых обновляются через REST API запросы

3. Определение доменов и границы контекстов
3.1. Домен Devices
    Поддомен: сенсоры температуры
3.2. Домен Services
    Поддомен: сервис управления отоплением

4. Проблемы монолитного решения
…
…
…
Если вы считаете, что текущее решение не вызывает проблем, аргументируйте свою позицию.

5. Визуализация контекста системы — диаграмма С4
Добавьте сюда диаграмму контекста в модели C4.

Чтобы добавить ссылку в файл Readme.md, нужно использовать синтаксис Markdown. Это делают так:

```markdown
[Диаграмма контекста исходной системы](https://www.plantuml.com/plantuml/duml/jPDHYzD04CVVyodMw4CFhWsAJqBXlFP1f69jA_SODidGBcvsrzrDIn51wwE7VWI_md5OJx6dNs7pZPnDsbXH42hseUdCxFpct_zaJuobsXOv9wVKi9ICQQuu13UOI7cH0PbPgyozAD9qqPaoEokIme1EfR0WR2ULUQGu5HxGDZRZB8bwTzj3dthwQ13br5ZGc8fxs46P0DrHU3O8Xg2D52qFEoQX--2-kQ_bkRl2vwMxA5TkxUFmcDmoIZCBtL1L7NTyYZFnh1lkfDMo_gebuJBP2HhGfIpiOsMP5AQJPpTdB8EudX3N0zjIjyrCBdxDrj_XKJ1U8YYFJsKXCggNhVGs_eq7G2qJKr8N3rKQ7f4N0S5Furbh0KbCbS8HPv2G-qfnbb8lFiJKGpgdVbO69jNTsiihTD4x-jwjonLnt_zexplYhZ5uNQxAL-x2VQvBvJcfwXliMcF1fzxWyxfywxuG_B5sd_3iXhXBuZuYSEFM_sKfwFBBhSyj0y98_wPC85UWgIqqa76LFDpc7Jo3EKjXkp_Ihw9_e3PhwoUjB45idrgQKEEPuL0QEzKmVZB0QE_jpirp7XlGSz2824R0jtVZv-eDs0dLKx1x7eHUzMGo7F-cjn5PAVObv7fi0smyHMIlq1h4Fla0OEDZe_GGNZpQ8thxHa0p4vrLrm-Fd838iEi7)
```


```markdown
[Текст ссылки](URL)
```
# Задание 2. Проектирование микросервисной архитектуры

В этом задании вам нужно предоставить только диаграммы в модели C4. Мы не просим вас отдельно описывать получившиеся микросервисы и то, как вы определили взаимодействия между компонентами To-Be системы. Если вы правильно подготовите диаграммы C4, они и так это покажут.

**Диаграмма контейнеров (Containers)**

```markdown
[Диаграмма контейнеров целевой системы](https://www.plantuml.com/plantuml/duml/lLRDRkCs43vNJp5hzE00JNneUocmmER7xQRDJn0tpMM1O2oDBJRyKJaZkqQnJzH7w6sVh2GbnN8NSUF5hds860s_7uw6GxvXGI-rqTahPNDT5mIbICK_Z4OUbqTp9MKzhPbyxgoGbQFScL6bqKRC8KkXrNHq-jtXJNnrTtanCiX2FhnwE0q8L9RyKHNvirS5pSA_S3R-xVpq-cho0Y6fAopyjsj15QA7ip3Za2klXBZJAsWHO_oaykFrrQ_7z-F9zUNuimgbTxWaTeOElrzdhLlL2EsyrjWk-kFmxxZ0pLZVwYWQu-UmdWhrR12NpuR22YlaDfnbDq72sM6K-WO6T-4n2CyFVqyCUe6tBWG-_0EyOY43UStYJ9hoTPEAruDaSd2GFNtX8LPLeBWVdy0xk7HJfGcEgqgh74Kv6-dRjCJXtNcVh0jiqgamx_Zc77v2eIMk8YncBZvFdJ5e2pWbAvk-qem-poFE7Z50VedFFiSbCUESuCIxn-qSPzDXCGs8s_7P-GJEJYBwhTC5Wv2fd4U_Wc6gFW8M5E83YEugyi5bi0W52lOLqbSC4fEKu8SJLziYi0nP1-e9-KHrWQl6brRsyVMWg-2cUlzl4muEuAyCmc-TYP9G7Wn7ys6ax1nQfRYUdt6H71R4kGzVH6ktP107nbabpgS5CGdKLLerUPJQqwVQ6qsrctRxAIpKrN9TnJhX8rE4n7orjgtLl6nzNyJXYrp7ZUsT1Ya94i4UZCvHgF4PAtPdcn7EUx2vbBniRDvZ69BVuhJoRg72633FYPDbhls2b0wwEK6EXZpkmtMplHhVPsdSzOKjzeEygMtiGCIm39QWH5yiSIzrQxbnU-L4pTekkCKhaoqOR6zoIdViitimImkotIPpy_dsvg3Td24W_4hACFDBsNkVPHyro5B7zjLynC_V8ON9nXJq6Xp4LyxleyHpD45xVrlAKqnc-8khVSZfDhcf7N_fjBw7yClMH_Z3-4yPilXul8edDBqAxn_CxJKfC6n2SHcj7zzFO2BEutm3XCi8oB9RqksDghaBXN5SO5fQd17ZAPBkDksEz_H7JImCC-TXWLeLQVE_gxoBBJVu_0_5mssw9ZGt4iA2H_VHnbeWS7UNdggUQiLbnql5MavP45UflCEraFLfs_eppJMfxVrJphsQajz4fRDhPr0yY7O6fKQrCwevFNQ6bOIxQrb-6IHXUiPA_GH2oDiBxa8Xe8trv5tb5Gf168dBdMvLdxB8ufy8EDKuLEZHa0Gzc7bdskEw1QRvJLqpBgW39Mjl0ajjzBy0)
```

**Диаграммы компонентов (Components)**

```markdown
[KAFKA](URL)
```


```markdown
[Heating Service](URL)
```

```markdown
[Light Service](URL)
```

```markdown
[Gate Service](URL)
```

```markdown
[Watcher Service](URL)
```

```markdown
[Device Gateway Service](URL)
```

**Диаграмма кода (Code)**

Добавьте одну диаграмму или несколько.

# Задание 3. Разработка ER-диаграммы

Добавьте сюда ER-диаграмму. Она должна отражать ключевые сущности системы, их атрибуты и тип связей между ними.