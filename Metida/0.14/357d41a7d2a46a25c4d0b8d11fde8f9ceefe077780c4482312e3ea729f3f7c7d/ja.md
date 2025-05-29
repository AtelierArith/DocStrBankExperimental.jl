StatsBase.confint(br::BootstrapResult, n::Int; level::Float64=0.95, method=:bp, metric = :coef, delrml = false)

ブートストラップ結果の信頼区間。

*method:

  * :bp - ブートストラップパーセンタイル;
  * :rbp - 逆ブートストラップパーセンタイル;
  * :norm - 正規分布;
  * :bcnorm - バイアス補正正規分布;
  * :jn - バイアス補正（ジャックナイフリサンプリング）。
