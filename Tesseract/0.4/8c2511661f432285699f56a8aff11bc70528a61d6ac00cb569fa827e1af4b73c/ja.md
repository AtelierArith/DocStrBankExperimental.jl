```
pix_write_pnm(
    pix::Pix
)::Union{Vector{UInt8}, Nothing}
```

PNM画像形式でバイト配列に画像を書き込みます。エラーが発生した場合は`false`が返されます。

**引数:**

| T   | 名前  | デフォルト | 説明            |
|:--- |:--- |:----- |:------------- |
| R   | pix |       | バイト配列に書き込む画像。 |
