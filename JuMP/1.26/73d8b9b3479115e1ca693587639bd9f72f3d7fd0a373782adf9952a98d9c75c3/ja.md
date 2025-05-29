```
copy_extension_data(data, new_model::AbstractModel, model::AbstractModel)
```

モデル `model` の拡張データ `data` のコピーを新しいモデル `new_model` の拡張データに返します。

`ext` フィールドにデータを格納する任意の JuMP 拡張のためにメソッドを追加する必要があります。

このメソッドは、JuMP 拡張を作成する開発者によってのみ実装されるべきです。JuMP のユーザーによって呼び出されることは決してありません。

!!! warning
    定義していない `data` の型に対してこのメソッドを実装することで型の盗用に関与しないでください！JuMP 拡張は、通常の Julia 型ではなく、自分が定義した型を `model.ext` に格納するべきです。

