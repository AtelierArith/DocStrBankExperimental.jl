```
simulate_observations_from_model(
    init_model, input_file_path, output_file_path; rng=Random.TaskLocalRNG()
) -> Matrix
```

`init_model` 関数によって初期化された状態空間モデルからの観測をシミュレートし、`input_file_path` の入力 YAML ファイルの `model` キーで指定されたパラメータを使用し、シミュレートされた観測と状態シーケンスを `output_file_path` の HDF5 ファイルに保存します。`rng` はモデルからシミュレートする際にランダム変数を生成するために使用する乱数生成器であり、再現可能な結果を保証するためにシード付きの乱数生成器を指定することができます。

`input_file_path` の入力 YAML ファイルには、`simulate_observations` キーがあり、その値は `seed` と `n_time_step` というキーを持つ辞書で、これらはそれぞれモデルから観測を生成するための時間ステップの数と、観測をシミュレートするために使用する乱数生成器の状態を初期化するためのシードに対応しています。

シミュレートされた観測シーケンスは、各時間ステップでの観測ベクトルに対応する列を持つ行列として返されます。
