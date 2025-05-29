```
interpolatable_field(xu,yu,xv,yv,f::EdgeData/NodePair)
```

グリッドデータ `f` の補間可能なバージョンを生成します。これは、`xu`、`yu`、`xv`、`yv` の座標に基づいています（これらは範囲形式である必要があります）。出力は、座標ペアを引数として関数として呼び出すことができます。
