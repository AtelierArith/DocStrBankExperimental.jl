```
ObjectScheme

ObjectScheme()
```

デフォルトのカラースキーム。`GreyScale`に似ていますが、`Number`用です。

他のグリッドオブジェクトは、合成オブジェクトから色を返すカスタムメソッドを定義できます：

```julia
DynamicGrids.to_rgb(::ObjectScheme, obj::MyObjectType) = ...
```

これは`ARGB32`値を返す必要があります。
