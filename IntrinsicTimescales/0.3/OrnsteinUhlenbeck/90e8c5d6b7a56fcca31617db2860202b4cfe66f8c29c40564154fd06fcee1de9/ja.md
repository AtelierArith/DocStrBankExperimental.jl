```
generate_ou_process(tau, true_D, dt, duration, num_trials; standardize=true)
```

単一のタイムスケールを持つオルンシュタイン-ウーレンベック過程を生成します

# 引数

  * `tau::Union{Real, Vector{<:Real}}`: OU過程のタイムスケール
  * `true_D::Real`: プロセスをスケーリングするためのターゲット分散
  * `dt::Real`: 時間ステップサイズ
  * `duration::Real`: 総時間長
  * `num_trials::Real`: 試行/軌道の数
  * `standardize::Bool=true`: 出力をtrue_Dに合わせて標準化するかどうか

# 戻り値

  * Matrix{Float64}: 次元が(num*trials, num*timesteps)の生成されたOU過程データ

# 注意事項

  * 内部でgenerate*ou*process_scimlを使用
  * SciMLソルバーが失敗した場合はNaN行列を返す
  * standardize=trueの場合、指定された分散を持つように出力を標準化する
