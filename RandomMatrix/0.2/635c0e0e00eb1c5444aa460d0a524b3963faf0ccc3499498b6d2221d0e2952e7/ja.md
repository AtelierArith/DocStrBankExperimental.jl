```julia
randOrthogonal(n::Int)
```

  * `n` by `n` のランダム直交行列を生成します
  * `rand(Haar(1,n))` と同等です。 [`Haar`](@ref) と [`COE`](@ref) を参照してください
  * ユニタリ行列の場合は、代わりに `randUnitary` または `rand(Haar(2,n))` を使用してください
  * アルゴリズムについては、[How to Generate Random Matrices from the Classical Compact Groups](http://www.ams.org/notices/200705/fea-mezzadri-web.pdf) を参照してください

# 例

3 by 3 のランダム直交行列を生成します 

```julia
randOrthogonal(3)

3×3 Matrix{Float64}:
 -0.875553  0.112448   0.469853
 -0.147915  0.863441  -0.482277
  0.459921  0.491757   0.739356
```
