```
run_algorithm!(optimizer::PB.BendersAlgorithm; output::Bool = true, run_gc::Bool = false)
```

Bendersアルゴリズムを使用してBendersAlgorithmのグラフを最適化します。キーワード引数`output`は、各イテレーションで上限/下限とギャップを印刷するかどうかを示します。`run_gc`は、各イテレーションの後にガーベジコレクタを実行するかどうかを示します。
