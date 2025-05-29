```
check(r; quiet=false, prenodes=false)
```

有理近似 `r` のドメインでの精度をチェックします。テストポイントとそれらのポイントでの誤差を返します。

# 引数

  * `r::Approximation`: 有理近似

# キーワード

  * `quiet::Bool=false`: @info 出力を抑制
  * `prenodes::Bool=false`: 近似のプレノードも返す

# 戻り値

  * `τ::Vector`: テストポイント
  * `err::Vector`: テストポイントでの誤差

詳細は [`approximate`](@ref) を参照してください。
