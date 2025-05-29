```
index!(sat::Sat; <kwargs...>)
index!(sat::Sat, ipart::SatInitialPartition; <kwargs...>)
index!(sat::Sat, ipart::RandomInitialPartition; <kwargs...>)
```

ツリー内の参照データセットのインデックスを作成します。初期パーティショニングスキームによって誘発される限られた形式のマルチスレッドをサポートしています。

# 引数

  * `sat`: メトリックデータ構造。
  * `ipart`: ツリーの初期パーティショニングスキーム。以下の種類のオブジェクトをサポートします：

      * `SatInitialPartition()`: 従来の構築、デフォルト値。各部分はSATパーティションであり、マルチスレッドセットアップでスレッドによって処理されます。
      * `RandomInitialPartition(nparts=Threads.nthreads(), shuffle=false)`: データセットを`nparts`の不連続部分に分割する構築（`shuffle=true`の場合はランダムに）。結果の構造は全体としてSATパーティショニングに違反し、良好なSATパーティションである一種のSATフォレストを作成します。ツリーの高さを制限し、マルチプロセッシングの目的に役立ちます。つまり、各部分はスレッドによって処理されます。

# キーワード引数

  * `sortsat`: 空間アクセスツリーを作成する戦略で、構築中の要素の順序に大きく依存します。以下を受け入れます：

      * `RandomSortSat()`: 子供がランダム化されます（デフォルト値）
      * `ProximalSortSat()`: 古典的アプローチで、近くの要素が最初に配置されます。
      * `DistalSortSat()`: 最近のアプローチで、遠くの要素が最初に配置されます。
  * `minleaf`: 空間アクセス分離を実行するための最小子供数（半空間パーティショニング）
