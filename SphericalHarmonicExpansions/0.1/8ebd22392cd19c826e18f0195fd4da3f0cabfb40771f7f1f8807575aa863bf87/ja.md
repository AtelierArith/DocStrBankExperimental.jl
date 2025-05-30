fastfunc(polynomial::Polynomial)

数値評価のための関数を生成します。引数は1つです。

多くの評価を行う予定がない場合は、標準的な方法を使用してください（詳細はTypedPolynomialsを参照）。評価の数が多い場合にのみ、この方法で生成された関数とトントンになることがあります。これは、ジャストインタイムコンパイルのオーバーヘッドによるものです。

# 例

```
julia> using SphericalHarmonics

julia> @polyvar x y z
(x, y, z)

julia> p = 15.0*x*y^2+7.5*x*z^13
7.5xz¹³ + 15.0xy²

julia> ps = fastfunc(p)

julia> r = [1.0,2.0,3.0]

julia> ps(r)
1.19574825e7
```
