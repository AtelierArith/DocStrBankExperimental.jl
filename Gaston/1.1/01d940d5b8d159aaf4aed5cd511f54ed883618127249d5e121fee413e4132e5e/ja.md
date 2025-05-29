```
scatter(x, y [, axes] [, curve] ; args...) -> Gaston.Figure
```

ベクトル `x` と `y` を使って散布図を作成します。`axes` と `curve` はそれぞれ軸と曲線の設定を指定します。

```
scatter(c, args...) -> Gaston.Figure
```

もし `c` が複素ベクトルであれば、`c` の実部と虚部の散布図を作成します。
