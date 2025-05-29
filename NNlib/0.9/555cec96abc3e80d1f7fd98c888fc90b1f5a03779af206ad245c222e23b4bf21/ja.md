```
upsample_linear(x::AbstractArray{T,3}, scale::Real; align_corners::Bool = true)
upsample_linear(x::AbstractArray{T,3}; size::Integer, align_corners::Bool = true)
```

配列 `x` の最初の次元を、提供された `scale` によってアップサンプリングし、線形補間を使用します。`scale` の代わりに、結果の配列 `size` をキーワード引数で直接指定することもできます。

出力のサイズは `(scale*S1, S2, S3)` に等しく、ここで `S1, S2, S3 = size(x)` です。
