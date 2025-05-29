```
pre_experiment(exp::Experiment; kwargs...)
pre_experiment(file_save::FileSave, exp; kwargs...)
pre_experiment(sql_save::SQLSave, exp; kwargs...)
```

この関数は、実験を成功裏に実行するために必要なすべてのセットアップを行います。これは、実験内の保存構造に基づいてディスパッチされます。

この関数は：

  * 基本的な実験ディレクトリを作成します。
  * 各保存タイプの詳細を初期化するために[`experiment_save_init`](@ref)を実行します。
  * [`add_experiment`](@ref)を実行します。
