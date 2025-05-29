```
bfacemask!(grid::ExtendableGrid,
                maskmin,
                maskmax,
                ireg;
                allow_new=true,
                tol=1.0e-10)
```

矩形マスクを介してグリッド境界ファセットの領域番号を編集します。`allow_new`がtrue（デフォルト）の場合、新しいファセットが追加されます。

iregは整数または関数`ireg(current_region)`である可能性があります。

ゼロの領域番号は境界面を削除します。

例: [Rectangle-with-multiple-regions](@ref)
