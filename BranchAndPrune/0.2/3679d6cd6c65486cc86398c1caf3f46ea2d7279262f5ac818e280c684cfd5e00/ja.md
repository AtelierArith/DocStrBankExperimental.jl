```
bpsearch(bp::BranchAndPruneSearch ; callback::Function)
```

分岐と剪定の探索を実行し、その結果をBranchAndPruneResultとして返します。

コールバック関数を指定することができ、これは各イテレーションで探索状態に対して呼び出されます。シグネチャは`callback(state::SearchState)::Bool`でなければなりません。`true`を返すと、探索が停止し、戻ります。
