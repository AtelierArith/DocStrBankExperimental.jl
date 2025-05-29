```
convert_arguments(P, x, y, f)::(Vector, Vector, Matrix)
```

ベクトル `x` と `y`、および関数 `f` を取り、`x` と `y` が span するグリッド上で `f` を適用します。これは `f.(x, y')` と同等です。`P` はプロットタイプ（オプションです）。
