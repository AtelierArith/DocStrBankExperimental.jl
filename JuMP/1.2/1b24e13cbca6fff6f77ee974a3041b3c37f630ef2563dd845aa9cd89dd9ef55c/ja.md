```
operator_warn(model::AbstractModel)
operator_warn(model::Model)
```

この関数は、`destructive_add!`を使用せずに2つのアフィン式が加算されるたびにモデルで呼び出され、2つの式のうち少なくとも1つが50項を超える場合に呼び出されます。

`Model`の場合、この関数が20,000回以上呼び出されると、警告が1回生成されます。
