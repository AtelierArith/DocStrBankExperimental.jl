```
cmp_test(seg1, seg2; <keyword arguments>)
```

2つのベクトルを比較します。最初にJarque–Beraを使用して分布の正規性をテストし、次にF検定を使用して分散をテストします。最後に、対応のあるt検定または対応のないt検定、または非パラメトリック検定（対応のあるデータにはウィルコクソン符号付き順位検定、対応のないデータにはマン・ホイットニーU検定）を適用します。置換ベースのテストも行われます。

# 引数

  * `s1::AbstractVector`
  * `s2::AbstractVector`
  * `paired::Bool`
  * `alpha::Float64=0.05`: 信頼水準
  * `type::Symbol=:auto`

      * `:auto`: テストを自動的に選択
      * `:perm`: 置換ベース
      * `:p`: パラメトリック
      * `:np`: 非パラメトリック
  * `exact::Bool=false`: trueの場合、正確なウィルコクソン検定を使用
  * `nperm::Int64=1000`: `:perm`メソッドのための置換の数
  * `verbose::Bool=true`: 詳細な出力を印刷

# 戻り値

置換ベースのテストの場合、名前付きタプルが含まれます：

  * `t::Tuple{perm_diff::Vector{Float64}, obs_diff::Float64}`: テスト結果（置換差、観測差）
  * `p1::Float64`: 一側p値
  * `p2::Float64`: 両側p値

それ以外の場合、名前付きタプルが含まれます：

  * `t::Union{OneSampleTTest, EqualVarianceTTest, UnequalVarianceTTest, ExactSignedRankTest, ApproximateSignedRankTest, ExactMannWhitneyUTest, ApproximateMannWhitneyUTest}`: 統計的検定
  * `ts::Tuple{Float64, String}`: テスト統計値と名前
  * `tc::Tuple{Float64, Float64}`: テスト統計の信頼区間
  * `df::Float64`: 自由度
  * `p::Float64`: p値
