```
Influent(states, sources::Vector; name, flowrate=nothing)
```

シミュレーションのためのインフルエントを提供するコンポーネントです。

ソースには3つの可能性があります：

  * 数値定数
  * 単一の数値時間引数を取る関数
  * `source.output`が有効な [`RealOutput`](@extref ModelingToolkitStandardLibrary.Blocks.RealOutput) ポートに評価される ODESystem。 [`ModelingToolkitStandardLibrary`](https://docs.sciml.ai/ModelingToolkitStandardLibrary/stable/API/blocks/#Source-Blocks) のすべてのソースブロックはこの特性を満たします。

# パラメータ：

  * `states`: フロー内のコンポーネント
  * `sources`: 値を定義するソースのベクター。
  * `flowrate`: フローレートを指定するための名前付きパラメータ。状態に含まれている場合は `nothing` に設定します。

# コネクタ：

  * `outflow`: `Influent` によって提供される流出。
