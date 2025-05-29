```
cl6(x::Real)::Real
```

実数角度 $x$ のための Clausen 関数 $\operatorname{Cl}_6(x)$ の値を返します。この関数は次のように定義されています。

$$
\operatorname{Cl}_6(x) = \Im[\operatorname{Li}_6(e^{ix})] = \sum_{k=1}^\infty \frac{\sin(kx)}{k^6}
$$

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl6(1.0)
0.855629273183937
```
