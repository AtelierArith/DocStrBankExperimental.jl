```
binom_test(x; verbose)
```

0.5に対する比率をテストします。

# 引数

  * `x::Vector{Bool}`: レベル0および1のカテゴリのベクトル
  * `verbose::Bool=true`: 詳細な出力を表示する

# 戻り値

名前付きタプルを含みます：

  * `x0::Int64`: レベル0のカウント
  * `x1::Int64`: レベル1のカウント
  * `p0::Float64`: レベル0の比率
  * `p1::Float64`: レベル1の比率
  * `ci0::Tuple{Float64, Float64}`: レベル1の比率の95%CI
  * `ci1::Tuple{Float64, Float64}`: レベル1の比率の95%CI
  * `p::Float64`: 二項検定のp値
