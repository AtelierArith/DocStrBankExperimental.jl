```
copy_extension_data(data, new_model::AbstractModel, model::AbstractModel)
```

モデル `model` の拡張データ `data` のコピーを新しいモデル `new_model` の拡張データに返します。

`ext` フィールドにデータを格納する任意の JuMP 拡張のためにメソッドを追加する必要があります。

!!! warning
    定義していない `data` の型に対してこのメソッドを実装することで型の略奪に関与しないでください！ JuMP 拡張は、通常の Julia 型ではなく、定義した型を `model.ext` に格納するべきです。

