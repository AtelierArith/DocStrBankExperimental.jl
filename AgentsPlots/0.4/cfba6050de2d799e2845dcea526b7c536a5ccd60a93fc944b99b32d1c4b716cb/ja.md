```
plotabm(model::ABM{<: ContinuousSpace}; ac, as, am, kwargs...)
plotabm(model::ABM{<: DiscreteSpace}; ac, as, am, kwargs...)
```

`model`を`scatter`プロットとして描画します。エージェントの形状、色、サイズはキーワード`ac, as, am`を介して設定されます。これらのキーワードは定数であってもよく、エージェントを受け取り、色/形状/サイズの有効な値を出力する関数であってもかまいません。

キーワード`scheduler = model.scheduler`はエージェントの描画順序を決定します（重なりがある場合にのみ重要です）。

キーワード`offset`は引数`offest(a::Agent)`を持つ関数です。これは、グリッドセル内に複数のエージェントが存在するシナリオを対象としており、プロットされたエージェントの位置にオフセット（`agent.pos`と同じタイプ）を追加します。

その他のキーワードは`Plots.scatter`に伝播され、プロットが返されます。
