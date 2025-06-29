```
csa_cor_vals(T::Int, p::Real, q::Real)
```

CSAプロセスの自己相関関数を、遅れ0, 1, ..., `T-1`でパラメータ`p`と`q`を用いて計算します。

# 引数

  * `T::Int`: 計算する遅れの数。
  * `p::Real`: CSAプロセスの最初のパラメータ。
  * `q::Real`: CSAプロセスの2番目のパラメータ。

# 出力

  * `acf::Array`: 遅れ0, 1, ..., `T-1`でパラメータ`p`と`q`を持つCSAプロセスの自己相関関数。

# 注意事項

この関数はcsa*var*vals()を使用して自己共分散関数を計算し、その後分散（最初に計算された値）で正規化します。

# 例

```julia
julia> csa_cor_vals(20, 0.4, 0.6)
```
