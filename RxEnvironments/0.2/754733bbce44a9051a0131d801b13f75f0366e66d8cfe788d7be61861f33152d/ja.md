```
subscribe_to_observations!(entity::AbstractEntity, actor)
```

`actor`を`entity`の観察に登録します。この関数が呼び出された後、`entity`に送信されたデータは`actor`によって受信されます。
