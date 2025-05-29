```
structure_constant_algebra(R::Ring, sctable::Array{_, 3}; one::Vector = nothing,
                                                          check::Bool = true)
```

与えられた次元 $(d, d, d)$ の配列と環 $R$ に対して、$R$ 上の $d$ 次元構造定数代数を返します。$R$ の基底 `e` は `e[i] * e[j] = sum(sctable[i,j,k] * e[k] for k in 1:d)` を満たします。

`check = false` でない限り、これは（時間がかかる）結合律と分配律のチェックを含みます。もし `one` が与えられた場合、指定された座標ベクトルを持つ要素を代数の単位元として記録します。

# 例

```jldoctest
julia> associative_algebra(QQ, reshape([1, 0, 0, 2, 0, 1, 1, 0], (2, 2, 2)))
Structure constant algebra of dimension 2 over QQ
```
