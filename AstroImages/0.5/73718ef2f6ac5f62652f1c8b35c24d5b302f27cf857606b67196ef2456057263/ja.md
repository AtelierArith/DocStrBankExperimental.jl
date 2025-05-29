```
copyheader(img::AstroImage, data) -> imgnew
```

`img`のヘッダーをコピーし、AbstractArray `data`のデータを使用して新しい画像を作成します。`imgnew`のヘッダーを変更しても、`img`のヘッダーには影響しません。参照: [`shareheader`](@ref)。
