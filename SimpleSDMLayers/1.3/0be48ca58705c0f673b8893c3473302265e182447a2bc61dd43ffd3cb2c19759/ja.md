```
reclassify(L::SDMLayer, rules::Pair...)
```

ルールに基づいてセルが更新されたレイヤーを返します。ルールは `(function) => value` の形式で与えられ、関数は `Bool` 値を返す必要があります。例えば、`reclassify(layer, (x -> abs(x)<=1)=>true)` は、値が -1;1 のすべてのセルに `true` の値を設定し、他のすべてのセルをマスクします。複数のルールを使用することができ、その場合は順次適用されます（後のルールが前のルールを上書きすることができます）。
