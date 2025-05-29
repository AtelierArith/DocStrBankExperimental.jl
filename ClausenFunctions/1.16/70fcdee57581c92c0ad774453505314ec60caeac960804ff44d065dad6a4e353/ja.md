```
cl3(x::Real)::Real
```

実数角度 $x$ のクローゼン関数 $\operatorname{Cl}_3(x)$ の値を返します。この関数は次のように定義されています。

$$
\operatorname{Cl}_3(x) = \Re[\operatorname{Li}_3(e^{ix})] = \sum_{k=1}^\infty \frac{\cos(kx)}{k^3}
$$

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl3(1.0)
0.44857300728001737
```
