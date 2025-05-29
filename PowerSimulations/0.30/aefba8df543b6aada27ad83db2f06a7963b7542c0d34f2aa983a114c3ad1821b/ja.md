```julia
run_parallel_simulation(
    build_function,
    execute_function;
    script,
    output_dir,
    name,
    num_steps,
    period,
    num_overlap_steps,
    num_parallel_processes,
    exeflags,
    force
)

```

ローカルコンピュータでパーティション化されたシミュレーションを並列に実行します。

# 引数

  * `build_function`: 構築されたシミュレーションを返す関数参照。
  * `execute_function`: シミュレーションを実行する関数参照。
  * `script::AbstractString`: $build_function$ と $execute_function$ を含むスクリプトへのパス。
  * `output_dir::AbstractString`: シミュレーション出力のためのパス
  * `name::AbstractString`: シミュレーション名
  * `num_steps::Integer`: シミュレーションの総ステップ数
  * `period::Integer`: 各シミュレーションパーティションのステップ数
  * `num_overlap_steps::Integer`: 各パーティションが前のパーティションと重なるステップ数
  * `num_parallel_processes`: 並列に実行するパーティションの数。何も指定しない場合はコアの数を使用します。
  * `exeflags`: Juliaプロジェクトへのパス。Distributed.addprocsに転送されます。
  * `force`: 出力ディレクトリが既に存在する場合は上書きします。
