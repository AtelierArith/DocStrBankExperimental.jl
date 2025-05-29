```
wait_for_jobs(jobids, output_dir, iter, experiment_dir, model_interface, module_load_str, model_run_func; verbose, hpc_kwargs, reruns=1)
```

ジョブのセットが完了するのを待ちます。ジョブが失敗した場合、最大`reruns`回まで再実行されます。

この関数は複数のジョブのステータスを監視し、失敗したジョブを指定された回数の`reruns`まで再実行することで失敗を処理します。エラーやジョブの完了ステータスをログに記録し、すべてのジョブが完了するまで進行を保証します。

引数:

  * `jobids`: ジョブIDのベクター。
  * `output_dir`: 出力用のディレクトリ。
  * `iter`: イテレーション番号。
  * `experiment_dir`: 実験用のディレクトリ。
  * `model_interface`: モデルへのインターフェース。
  * `module_load_str`: 必要なモジュールをロードするためのコマンド。
  * `model_run_func`: モデルを実行するための関数。
  * `verbose`: trueの場合、詳細なログを印刷します。
  * `hpc_kwargs`: HPCジョブのパラメータ。
  * `reruns`: 失敗したジョブを再実行する回数。
