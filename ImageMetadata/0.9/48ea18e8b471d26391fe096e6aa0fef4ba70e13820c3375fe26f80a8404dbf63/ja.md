```
arraydata(img::ImageMeta) -> array
```

`img`からプロパティ辞書を省略してデータを抽出します。`array`は`img`とストレージを共有しているため、一方の変更はもう一方に影響を与えます。

参照: [`properties`](@ref).
