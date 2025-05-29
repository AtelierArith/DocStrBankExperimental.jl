```
left_crop(str::AbstractString, crop_width::Int) -> String, String
```

`str`の左側の文字を切り取って、表示幅が`crop_width`の表示単位だけ減少した文字列を返します。

# 返り値

  * `String`: 切り取られた部分のANSIエスケープシーケンス（非表示文字列）。
  * `String`: 切り取られた文字列。

# 拡張ヘルプ

## 例

```julia-repl
julia> left_crop("\e[1mPlease, crop this string.", 8)
("\e[1m", "crop this string.")
```
