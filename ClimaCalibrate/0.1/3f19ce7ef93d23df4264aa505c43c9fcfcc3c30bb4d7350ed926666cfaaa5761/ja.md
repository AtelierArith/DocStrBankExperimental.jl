```
add_workers(
    nworkers;
    device = :gpu,
    cluster = :auto,
    kwargs...
)
```

現在のJuliaセッションに`nworkers`のワーカープロセスを追加し、利用可能なコンピューティング環境を自動的に検出して構成します。

# 引数

  * `nworkers::Int`: 追加するワーカープロセスの数。
  * `device::Symbol = :gpu`: 対象の計算デバイスタイプ、`:gpu`（1 GPU、4 CPUコア）または`:cpu`（1 CPUコア）のいずれか。
  * `cluster::Symbol = :auto`: 使用するクラスタ管理システム。オプション:

      * `:auto`: 利用可能なクラスタ環境を自動検出（SLURM、PBS、またはローカル）
      * `:slurm`: SLURMスケジューラの強制使用
      * `:pbs`: PBSスケジューラの強制使用
      * `:local`: ローカル処理の強制使用（標準の`addprocs`）
  * `kwargs`: その他のkwargsは`addprocs`に直接渡すことができます。
