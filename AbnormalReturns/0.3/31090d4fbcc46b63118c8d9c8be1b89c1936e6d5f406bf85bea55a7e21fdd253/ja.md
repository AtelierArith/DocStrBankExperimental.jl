```
function BasicReg(
    resp::AbstractVector,
    pred::AbstractMatrix,
    yname::String,
    xnames::SVector{N, String},
    f::FormulaTerm{L,R};
    save_residuals::Bool=false,
    minobs=1
)::BasicReg{L,R} where {L,R}
```

## 引数

  * resp::AbstractVector{Float64}: 線形回帰における「Y」または応答
  * pred::AbstractMatrix{Float64}: 線形回帰における「X」行列
  * yname::String: 応答変数の名前
  * xnames::SVector{N, String}: 予測変数の名前
  * f::FormulaTerm{L,R}: 結果の構造体に保存されたStatsModels.jlの式
  * save_residuals::Bool=false: 回帰からの残差ベクトルを保存するかどうか。回帰の数が多い場合、これにより速度が大幅に低下する可能性があります
  * minobs::Int=1: 回帰を実行するための応答ベクトルの最小長さ。応答ベクトルの長さが予測行列の列数以下の場合、回帰は実行されません。

BasicRegは意図的に単純な線形回帰です。ベクトルのビューが渡される場合、最小限のアロケーションを生成しようとします。
