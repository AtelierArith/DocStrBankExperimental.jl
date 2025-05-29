```
issymmetric(g::IndexedBiDiGraph) -> Bool
```

有向グラフが対称であるかどうかをテストします。すなわち、各有向辺 `i=>j` に対して、辺 `j=>i` も存在するかどうかを確認します。
