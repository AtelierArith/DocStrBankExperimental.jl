```
plot([x,] y, [z,] [axes,] [supp,] [dims,] [h,] [curve]) -> Gaston.Figure
```

データ `x`、`y`、およびオプションで `z` と `supp` を、`dims` で指定された二次元または三次元でプロットし、`axes` の設定と `curve` の設定を使用して、ハンドル `h` の図に描画します。

`x` が省略された場合、`x=1:length(t)` が仮定されます。

```
plot(x, f::Function, args...) -> Gaston.Figure
```

`y = f.(x)` と仮定します。

```
plot(c, args...) -> Gaston.Figure
```

`c` が複素ベクトルの場合、実部を虚部に対してプロットします。

```
plot(P::Matrix{Union{Gaston.Figure}, Nothing}) -> Gaston.Figure
```

`P` のレイアウトで 'muliplot' を作成します。新しい図を返します。
