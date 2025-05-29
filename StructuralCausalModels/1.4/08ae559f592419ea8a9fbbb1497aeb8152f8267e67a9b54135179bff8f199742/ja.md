# `adjustment_sets`

```julia
adjustment_sets(dag, f, l; debug)

```

共分散調整頂点集合を計算します。

### 必要な引数

```julia
* `dag::DAG`                           : DAG
* `f::Symbol`                          : 開始変数
* `l::Symbol`                          : 終了変数
```

### オプションの引数

```julia
* `debug::Bool`                        : デバッグトレースを表示
```

### 戻り値

```julia
* `adjustmentsets=Vector{Symbol}[]`    : 調整セットの配列
```

# 拡張ヘルプ

### 謝辞

元の著者                        : Rob J Goedman

### ライセンス

ライセンスの種類: MIT。

APIの一部であり、エクスポートされています。
