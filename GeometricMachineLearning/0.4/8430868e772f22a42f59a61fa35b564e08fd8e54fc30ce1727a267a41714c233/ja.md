```
VolumePreservingFeedForward(dim)
```

特定のシステム次元のための体積保存フィードフォワードニューラルネットワークのインスタンスを作成します。    

このアーキテクチャは、[`VolumePreservingLowerLayer`](@ref) と [`VolumePreservingUpperLayer`](@ref) の合成です。 

# 引数

コンストラクタに次の追加引数を提供できます：

2. `n_blocks::Int = 1`: ニューラルネットワーク内のブロックの数（線形層と非線形層を含む）。
3. `n_linear::Int = 1`: 1つのブロック内の線形 `VolumePreservingLowerLayer` と `VolumePreservingUpperLayer` の数。
4. `activation = tanh`: ブロック内の非線形層のための活性化関数。

次のキーワード引数があります：

  * `init_upper::Bool = false`: 最初の層が下層か上層かを指定します。
