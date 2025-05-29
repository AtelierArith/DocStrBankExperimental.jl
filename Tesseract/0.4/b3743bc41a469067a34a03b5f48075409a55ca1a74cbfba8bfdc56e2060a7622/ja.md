```
pix_write_implied_format(
    filename::AbstractString,     # 書き込むファイルの名前。
    pix::Pix;                     # 書き込む画像。
    quality::Integer  = Int32(75), # 画像がJPEGの場合、エンコードする品質。
    progressive::Bool = false     # 画像がJPEGの場合、プログレッシブエンコーディングを使用するか？
)::Bool
```

ファイル拡張子に基づいて画像をファイルに書き込みます。品質とプログレッシブパラメータは、画像タイプがJPEGの場合にのみ使用されます。成功した場合はtrueを、失敗した場合はfalseを返します。
