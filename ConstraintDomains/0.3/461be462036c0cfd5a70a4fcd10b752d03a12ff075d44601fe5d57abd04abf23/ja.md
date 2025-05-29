```
explore!(explorer::Explorer)
```

`Explorer`オブジェクトで定義された探索空間を探索します。

この関数は、`Explorer`オブジェクトに指定された設定に従って探索空間を探索します。見つかった解と非解で`Explorer`の状態を更新します。

# 引数

  * `explorer`: 問題定義と探索設定を含む`Explorer`オブジェクト。

# 戻り値

何も返しません。`Explorer`の状態はインプレースで更新されます。

# 例

```julia
explorer = Explorer(concepts, domains)
explore!(explorer)
println("見つかった解の数: ", length(explorer.state.solutions))
```
