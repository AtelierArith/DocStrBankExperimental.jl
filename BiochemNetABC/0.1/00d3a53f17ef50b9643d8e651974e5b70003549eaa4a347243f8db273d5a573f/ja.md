`volatile_simulate(sm::SynchronizedModel; p, verbose)`

オートマトンと同期したモデルをシミュレートしますが、パフォーマンスを向上させるためにシミュレーションの値を保存しません。シミュレーションの最後の状態 `S::StateLHA` を返し、軌跡 `σ::SynchronizedTrajectory` は返しません。
