```
model_run(backend, iter, member, output_dir, experiment_dir; model_interface, verbose, hpc_kwargs)
```

与えられたジョブスケジューラで単一のフォワードモデルを実行するコマンドを構築して実行します。

`backend` に基づいて [`slurm_model_run`](@ref) または [`pbs_model_run`](@ref) を実行します。

引数:

  * iter: イテレーション番号
  * member: メンバー番号
  * output_dir: キャリブレーション実験の出力ディレクトリ
  * project_dir: 実験の Project.toml を含むディレクトリ
  * model_interface: モデルインターフェースファイル
  * module*load*str: 必要なモジュールをロードするコマンド
  * hpc_kwargs: ジョブのリソースを含む辞書。 [`kwargs`](@ref) を使用して簡単に生成できます。
