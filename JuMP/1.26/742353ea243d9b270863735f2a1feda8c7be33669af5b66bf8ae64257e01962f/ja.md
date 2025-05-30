```
operator_warn(model::AbstractModel)
operator_warn(model::GenericModel)
```

この関数は、`destructive_add!`を使用せずに2つのアフィン式が加算されるたびにモデルで呼び出され、2つの式のうち少なくとも1つが50項を超えている場合に呼び出されます。

`Model`の場合、この関数が20,000回以上呼び出されると、警告が1回生成されます。

このメソッドは、JuMP拡張を作成する開発者によってのみ実装されるべきです。JuMPのユーザーによって呼び出されるべきではありません。
