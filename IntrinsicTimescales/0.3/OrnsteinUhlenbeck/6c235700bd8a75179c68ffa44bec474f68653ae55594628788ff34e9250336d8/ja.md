```
generate_ou_process_sciml(tau, true_D, dt, duration, num_trials, standardize=true)
```

DifferentialEquations.jlを使用してオルンシュタイン-ウーレンベック過程を生成します。

# 引数

  * `tau::Union{T, Vector{T}}`: OU過程の時間スケール
  * `true_D::Real`: スケーリングのためのターゲット分散
  * `dt::Real`: 時間ステップサイズ
  * `duration::Real`: 総時間長
  * `num_trials::Integer`: 試行/軌道の数
  * `standardize::Bool=true`: 出力を標準化するかどうか

# 戻り値

  * `Tuple{Matrix{Float64}, ODESolution}`: 

      * スケーリングされたOU過程データ
      * 完全なSDE解オブジェクト

# 注意事項

  * 効率のためにSOSRAソルバーを使用
  * num_trialsに基づいて静的配列と動的配列の間で切り替え
  * standardize=trueの場合、出力をtrue_Dに合わせて標準化
