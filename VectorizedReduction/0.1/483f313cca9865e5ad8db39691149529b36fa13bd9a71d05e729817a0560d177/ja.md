```
vvextrema([f=identity], A::AbstractArray; [dims=:], [init=(mn,mx)])
```

与えられた `dims` にわたって `A` の各要素に `f` を適用することによって最小値と最大値を計算し、`init` の2タプルのそれぞれの引数によって初期化された `mn` と `mx` を使用します。これらは任意の組み合わせの値（`<:Number`）または単一の型引数を受け入れる関数であることができます。

# 警告

`NaN` 値は処理されません！

# 例

```jldoctest
julia> A = reshape(Vector(1:2:16), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  5
 3  7

[:, :, 2] =
  9  13
 11  15

julia> vvextrema(abs2, A, dims=(1,2), init=(typemax, 100))
1×1×2 Array{Tuple{Int64, Int64}, 3}:
[:, :, 1] =
 (1, 100)

[:, :, 2] =
 (81, 225)

julia> vvextrema(abs2, A, init=(typemax, 100))
(1, 225)
```
