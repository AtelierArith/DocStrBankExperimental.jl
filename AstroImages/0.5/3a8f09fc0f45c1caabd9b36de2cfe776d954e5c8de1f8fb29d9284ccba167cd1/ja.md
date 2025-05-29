```
shareheader(img::AstroImage, data) -> imgnew
```

`img`のヘッダ辞書を再利用しつつ、AbstractArray `data`のデータを使用して新しい画像を作成します。2つの画像はヘッダが同期しており、一方を変更するともう一方にも影響があります。詳細は[`copyheader`](@ref)を参照してください。
