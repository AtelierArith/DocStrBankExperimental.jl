MPIで実行するためのフラグ。使用する前に、[`setup_mpi`](@ref)を一度呼び出す必要があります。

フィールド:

  * `n_threads`: MPIプロセスごとのスレッド数、デフォルトは1。
  * `walltime`: ウォールタイム制限、デフォルトは00:30:00（すなわち30分）。
  * `n_mpi_processes`: MPIプロセスの数、デフォルトは2。
  * `memory`: 各MPIプロセスに割り当てられるメモリ、デフォルトは8gb。
  * `dependencies`: 子プロセスに必要なJuliaモジュール（`Module`型の場合）またはインクルードするパス（`String`型の場合）。
  * `mpiexec_args`: mpiexecに渡される追加の引数。
