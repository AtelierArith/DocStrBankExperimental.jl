```
csa_ma_coefs(p::Real, q::Real, maxlags::Int)
```

CSAプロセスのMA係数を、パラメータ`p`と`q`でラグ0, ..., `maxlags-1`に対して計算します。

# 引数

  * `p::Real`: CSAプロセスのパラメータp。
  * `q::Real`: CSAプロセスのパラメータq。
  * `maxlags::Int`: 計算するラグの数。

# 出力

  * `ma_coefs::Array`: CSAプロセスのMA係数で、パラメータ`p`と`q`に対してラグ0, ..., `maxlags-1`の値を持つ。

# 注意事項

MA係数は速度のために再帰的な公式を使用して計算されます。ゼロラグ係数は含まれており、理論的には1です。

# 例

```julia
julia> csa_ma_coefs(1.4, 1.4, 5)
```
