```
cl2(x::Real)::Real
```

実数角度 $x$ のクローゼン関数 $\operatorname{Cl}_2(x)$ の値を返します。クローゼン関数は次のように定義されます。

$$
\operatorname{Cl}_2(x) = -\int_0^x \log|2\sin(t/2)| dt
$$

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl2(1.0)
1.0139591323607684
```
