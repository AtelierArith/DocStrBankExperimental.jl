```
Jet(;dom, rng, f!, df!, df′!, upstate!, s)
```

`dom::JetAbstractSpace` のドメイン、`rng::JetSAbstractpace` のレンジを持つ `Jet` を返します。前方マッピング `f!::Function`、線形化された前方マッピング `df!::Function`、線形化された随伴マッピング `df′!::Function`、ヤコビアン状態修正関数 `upstate!::Function`、および状態 `s::NamedTuple` を持ちます。

ジェットは関数 `f!` とその線形化（前方 `df!` および随伴 `df′!`）を点について記述します。

`f!` または `df!` のいずれかが指定され、`df′!` が指定されていない場合、`f!=df!=df′!` と仮定します。これは、演算子が線形で自己随伴であることを意味します。

`f!` と `df!` が指定されているが `df′!` が指定されていない場合、`df′!=df!` と仮定します。これは、演算子が非線形で自己随伴であることを意味します。

# 例

自己随伴の線形化を持つ非線形マッピングを考えます $f(x)=x^2$

```julia
using Jets
g!(m) = m.^2
dg!(δm; mₒ) = @. 2*mₒ*δm
jet = Jet(;dom=JetSpace(Float64,2), rng=JetSpace(Float64,2), f! = g!, df! = dg!)
```
