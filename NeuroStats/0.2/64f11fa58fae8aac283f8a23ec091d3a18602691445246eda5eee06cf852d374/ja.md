```
binom_test(p, n; verbose)
```

0.5に対する比率をテストします。

# 引数

  * `p::Float64`: レベル1の観測値の比率
  * `n::Int64`: 観測値の数
  * `verbose::Bool=true`: 詳細な出力を表示するかどうか

# 戻り値

次の内容を含む名前付きタプル:

  * `x0::Int64`: レベル0のカウント
  * `x1::Int64`: レベル1のカウント
  * `p0::Float64`: レベル0の比率
  * `p1::Float64`: レベル1の比率
  * `ci0::Tuple{Float64, Float64}`: レベル1の比率の95%CI
  * `ci1::Tuple{Float64, Float64}`: レベル1の比率の95%CI
  * `p::Float64`: 二項検定のp値
