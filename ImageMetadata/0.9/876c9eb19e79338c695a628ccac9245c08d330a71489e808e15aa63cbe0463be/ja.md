```
copyproperties(img::ImageMeta, data) -> imgnew
```

新しい「画像」を作成し、`img`のプロパティ辞書をコピーしますが、AbstractArray `data`のデータを使用します。`imgnew`のプロパティを変更しても、`img`のプロパティには影響しません。

参照: [`shareproperties`](@ref).
