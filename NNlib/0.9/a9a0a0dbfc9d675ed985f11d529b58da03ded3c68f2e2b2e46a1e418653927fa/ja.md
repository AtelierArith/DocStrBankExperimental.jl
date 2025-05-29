```
upsample_trilinear(x::AbstractArray{T,5}, scale::NTuple{3,Real}; align_corners::Bool = true)
upsample_trilinear(x::AbstractArray{T,5}; size::NTuple{3,Integer}, align_corners::Bool = true)
```

配列 `x` の最初の3次元を、`scale` に格納されたアップサンプル係数を使用してトリリニア補間でアップサンプリングします。`scale` の代わりに、結果の画像 `size` をキーワード引数で直接指定することもできます。

出力のサイズは `(scale[1]*S1, scale[2]*S2, scale[3]*S3, S4, S5)` に等しく、ここで `S1, S2, S3, S4, S5 = size(x)` です。

# 例

```julia
upsample_trilinear(x, (2, 3, 4))
upsample_trilinear(x; size=(4, 9, 11))  # 出力サイズを指定する
upsample_trilinear(x, (2.5, 3.5, pi))  # 整数以外のスケーリング係数も許可されます
```
