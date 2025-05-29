```
shareproperties(img::ImageMeta, data) -> imgnew
```

新しい「画像」を作成し、`img`のプロパティ辞書を再利用しますが、AbstractArray `data`のデータを使用します。2つの画像はプロパティが同期しており、一方を変更するともう一方にも影響します。

参照: [`copyproperties`](@ref)。
