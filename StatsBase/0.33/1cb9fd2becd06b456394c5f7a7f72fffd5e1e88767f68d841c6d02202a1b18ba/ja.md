```
mean(A::AbstractArray, w::AbstractWeights[, dims::Int])
```

配列 `A` の加重平均を重みベクトル `w`（型 `AbstractWeights`）を用いて計算します。`dim` が指定されている場合は、次元 `dims` に沿った加重平均を計算します。

# 例

```julia
n = 20
x = rand(n)
w = rand(n)
mean(x, weights(w))
```
