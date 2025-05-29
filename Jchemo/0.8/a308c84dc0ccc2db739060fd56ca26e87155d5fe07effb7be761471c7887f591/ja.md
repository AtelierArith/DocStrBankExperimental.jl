```
softmax(x::AbstractVector)
softmax(X::Union{Matrix, DataFrame})
```

ソフトマックス関数。

  * `x` : 変換するベクトル。
  * `X` : 行が変換される行列。

ベクトルvを考えます：

  * 'softmax'(v) = exp.(v) / sum(exp.(v))

## 例

```julia
using Jchemo

x = 1:3
softmax(x)

X = rand(5, 3)
softmax(X)
```
