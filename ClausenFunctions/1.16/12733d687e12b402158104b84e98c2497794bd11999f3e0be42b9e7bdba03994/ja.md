```
cl5(x::Real)::Real
```

実数角度 $x$ のためのクローゼン関数 $\operatorname{Cl}_5(x)$ の値を返します。この関数は次のように定義されます。

$$
\operatorname{Cl}_5(x) = \Re[\operatorname{Li}_5(e^{ix})] = \sum_{k=1}^\infty \frac{\cos(kx)}{k^5}
$$

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl5(1.0)
0.5228208076420943
```
