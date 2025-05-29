```
scatter3(x, y, z, [axes,] [curve,], args...) -> Gaston.Figure
```

ベクトル `x`、`y`、および `z` を使用して3-D散布図を作成します。`axes` と `curve` は、それぞれ軸と曲線の設定を指定します。

```
scatter3(x, f1::Function, f2::Function, args...) -> Gaston.Figure
```

`x`、`f1.(x)`、および `f2.(x)` の散布図を作成します。
