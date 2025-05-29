```
setup_reservoir_simulator(models, initializer, parameters = nothing; <keyword arguments>)
```

# 引数

  * `models`: 単一のモデルまたはマルチモデル用のキー :Reservoir を持つ Dict
  * `initializer`: state0 を設定するために使用され、`model` と互換性がある必要があります
  * `parameters`: 初期化されたパラメータで、提供される場合は `model` と互換性がある必要があります

# キーワード引数

  * `split_wells`: 各井戸に施設モデルを追加します（ドメイン分解と MPI 解決に必要）
  * `assemble_wells_together`: 井戸を複数のスパース行列に分割するオプション（false 引数は実験的）
  * `specialize=false`: より高速な実行のためにストレージの深い特化を使用しますが、コンパイル時間が大幅に増加します

追加のキーワード引数は、`JutulCase` を入力として使用するこの関数のバージョンに文書化されています。
