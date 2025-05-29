```
calibrate(backend, ekp::EnsembleKalmanProcess, ensemble_size, n_iterations, prior, output_dir)
calibrate(backend, ensemble_size, n_iterations, observations, noise, prior, output_dir; ekp_kwargs...)
```

指定されたバックエンドで完全なキャリブレーションを実行します。

EKP構造体が指定されていない場合、初期化時に構築されます。EKPキーワード引数はEKPコンストラクタに渡されますが、多くのキーワードを使用する場合は、EKPオブジェクトを構築して`calibrate`に渡すことをお勧めします。

利用可能なバックエンド: WorkerBackend, CaltechHPCBackend, ClimaGPUBackend, DerechoBackend, JuliaBackend

Derecho、ClimaGPU、およびCaltechHPCバックエンドは、特定の高性能コンピューティングクラスターで実行するように設計されています。WorkerBackendはDistributed.jlを使用して、ワーカー上でフォワードモデルを実行します。

## HPCバックエンドのキーワード引数

  * `model_interface`: モデルインターフェースファイルへのパス。
  * `hpc_kwargs`: ジョブスケジューラに渡されるHPCクラスター用のリソース引数の辞書。
  * `verbose::Bool`: 詳細なログを有効にします。
  * `EnsembleKalmanProcess`コンストラクタの任意のキーワード引数（例: `scheduler`）
