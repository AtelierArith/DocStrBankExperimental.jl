```
conley_index(lc::LefschetzComplex, subcomp::Vector{String})
```

Lefschetz複体の部分集合のコンリー指数を決定します。

部分集合`subcomp`が局所的に閉じていない場合、関数はエラーを発生させます。計算はLefschetz複体の境界行列に関連付けられた体上で行われます。
