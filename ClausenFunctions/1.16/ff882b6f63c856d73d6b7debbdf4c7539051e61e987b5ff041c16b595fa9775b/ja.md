```
cl4(x::Real)::Real
```

実数角度 $x$ のための Clausen 関数 $\operatorname{Cl}_4(x)$ の値を返します。この関数は次のように定義されます。

$$
\operatorname{Cl}_4(x) = \Im[\operatorname{Li}_4(e^{ix})] = \sum_{k=1}^\infty \frac{\sin(kx)}{k^4}
$$

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl4(1.0)
0.8958052386793799
```
