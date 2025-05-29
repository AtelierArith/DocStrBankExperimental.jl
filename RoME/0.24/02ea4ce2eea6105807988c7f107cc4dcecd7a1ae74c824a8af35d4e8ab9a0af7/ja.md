```julia
accumulateDiscreteLocalFrame!(mpp, DX, Qc; ...)
accumulateDiscreteLocalFrame!(mpp, DX, Qc, dt; Fk, Gk, Phik)

```

オドメトリファクターをODEを統合するかのように進めます – すなわち、$X_2 = X_1 ⊕ ΔX$。連続ドメインプロセスノイズ密度 `Qc` を受け入れ、内部で離散プロセスノイズ Qd に統合されます。$DX$ はこの関数の前にすでに逐次的に統合されていると仮定されます。完全に連続的なシステム伝播については、関連する `accumulateContinuousLocalFrame!` を参照してください。

ノート

  * この更新は同じ参照フレームに留まりますが、時間の経過に伴う測定値を累積するかのようにローカルベクトルを更新します。
  * カルマンフィルターはノイズ伝播に使用されます: $Pk1 = F*Pk*F' + Qdk$
  * Chirikjian, Vol.II, 2012, p.35 より: ヤコビアン SE(2), Jr = [cθ sθ 0; -sθ cθ 0; 0 0 1] – すなわち、dSE2/dX' = SE2([0;0;-θ])
  * `DX = dX/dt*Dt`
  * `{}^b Qc = {}^b [x;y;yaw] = [fwd; sideways; rotation.rate]` のプロセスノイズを仮定

開発ノート

  * TODO ここで多くの操作はインプレースで行うことができます。

関連

accumulateContinuousLocalFrame!, accumulateDiscreteReferenceFrame!, [`accumulateFactorMeans`](@ref) ```
