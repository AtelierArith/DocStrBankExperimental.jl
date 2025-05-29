```
run_node!(
    node::DamNode, climate::Climate, ts::Int;
    inflow=nothing, extraction=nothing, exchange=nothing
)::Nothing
```

特定のノードを指定された時間ステップで実行します。

# 引数

  * `node` : DamNode
  * `climate` : 気候データセット
  * `ts` : 現在の時間ステップ
  * `inflow` : 上流ノードからの流入の時間系列。
  * `extraction` : 水の注文の時間系列（`_releases`の列を期待）
  * `exchange` : 地下水フラックスの時間系列
