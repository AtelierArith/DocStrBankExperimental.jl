```
size_c2g(; <keyword arguments>)
```

連続変数（グループ1対グループ2）の必要サンプルサイズを計算します。

# 引数

  * `m1::Real`: 研究グループ1の平均
  * `s1::Real`: 研究グループ1の標準偏差
  * `m2::Real`: 研究グループ2の平均（期待値）
  * `r::Int64=1`: 登録比 – グループ2とグループ1の登録の比率
  * `alpha::Float64=0.05`: 第I種過誤の確率
  * `power::Float64=0.8`: グループ間の差を検出する能力（power = 1 - beta、ここでbetaは第II種過誤の確率）

# 戻り値

次の内容を含む名前付きタプル：

  * `n1::Int64`: グループ1のサンプルサイズ
  * `n2::Int64`: グループ2のサンプルサイズ
