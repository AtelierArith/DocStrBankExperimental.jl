```
VolumePreservingTransformer(sys_dim, seq_length)
```

与えられたシステム次元とシーケンス長のための体積保存変換器のインスタンスを作成します。

# 引数

以下はキーワード引数です：

  * `n_blocks::Int = 1`: 1つの変換器ユニット内のブロック数（線形層と非線形層を含む）。
  * `n_linear::Int = 1`: 1つのブロック内の線形 `VolumePreservingLowerLayer` と `VolumePreservingUpperLayer` の数。
  * `L::Int = 1`: 変換器ユニットの数。
  * `activation = tanh`: 活性化関数。
  * `init_upper::Bool = false`: ネットワークが最初に $q$ コンポーネントに作用するかどうかを指定します。
  * `skew_sym::Bool = false`: 重み行列が斜め対称か任意かを指定します。
