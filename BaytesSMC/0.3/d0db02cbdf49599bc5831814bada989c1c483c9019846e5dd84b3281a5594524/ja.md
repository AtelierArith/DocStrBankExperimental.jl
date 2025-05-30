```julia
struct SMCDefault{F<:Function, T<:BaytesCore.ResamplingMethod, B<:BaytesCore.UpdateBool, C<:BaytesCore.UpdateBool, U<:BaytesCore.UpdateBool}
```

SMCコンストラクタのデフォルト引数。

# フィールド

  * `Ntuning::Int64`: サンプラーを構築する際に使用されるチューニングステップの数。
  * `resamplingmethod::BaytesCore.ResamplingMethod`: リサンプリングチェーンの閾値。
  * `resamplingthreshold::Float64`: リサンプリングチェーンの閾値。リサンプリングを常に適用する場合は1.0に設定します。
  * `jitterfun::Function`: ジッタリングを停止できるかどうかを判断するためにパラメータの相関ベクトルに適用される関数。
  * `jitteradaption::BaytesCore.UpdateBool`: 固定数のジッターステップが適用されるか、ジッタリングがパラメータの相関に基づいているかのブール値。
  * `jitterdiagnostics::BaytesCore.UpdateBool`: ジッターステップでの診断がSMCDiagnosticsに記録されるべきかのブール値。
  * `jitterthreshold::Float64`: ジッタリングされたモデルパラメータのjitterfun(correlation)に対する停止閾値。
  * `jittermin::Int64`: 最小ジッタリングステップ数。
  * `jittermax::Int64`: 最大ジッタリングステップ数。
  * `generated::BaytesCore.UpdateBool`: 対応するモデルのためにgenerate(_rng, objective)がPF Diagnosticsに保存されるべきかのブール値。
