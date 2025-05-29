```
TimedCallback(affect, executiontimes; offset=0.0, initialize, finalize)
```

シミュレーション時間が `executiontimes` に指定されたポイントのいずれかより大きくなると、[`prepropagate!`](@ref) フック内で関数 `affect` をシミュレーション状態に対して呼び出す一般的なコールバックです。 `executiontimes` はインデックス可能で、昇順にソートされている必要があります（同じ要素が複数あっても問題ありません）。 kwarg `offset` は、すべての実行時間を指定された量だけシフトするオプションです。 `initialize` および `finalize` 関数は、コールバックが最初に実行されるときと、シミュレーションが正常に終了したときにそれぞれ呼び出されます。
