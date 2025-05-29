```
polycor(X::Union{AbstractDataFrame, AbstractMatrix}; lower_tri = false)
```

Xからポリコリック相関行列を推定します。

# 引数

  * `X` カテゴリカルベクトルを含む行列。
  * `lower_tri` 論理値。

# 例

```julia

using Distributions
# サポート関数
function discretize(x, th)
    sum(th .< x)
end
# シミュレーションデータを生成。
raw = rand(MvNormal([0, 0], [1 .5; .5 1]), 10000)'
τ1 = sort!(rand(Uniform(-2, 2), 3))
τ2 = sort!(rand(Uniform(-2, 2), 4))
obs = [discretize.(raw[:, 1], Ref(τ1)) discretize.(raw[:, 2], Ref(τ2)) ]

polycor(obs)
```
