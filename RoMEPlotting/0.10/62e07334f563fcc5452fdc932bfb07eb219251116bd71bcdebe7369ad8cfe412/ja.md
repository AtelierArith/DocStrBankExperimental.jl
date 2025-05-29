```julia
plotLocalProductCylinder(
    fgl,
    lbl;
    N,
    levels,
    show,
    dirpath,
    mimetype,
    sidelength,
    scale
)

```

円筒多様体に対してのみ、因子グラフ内の隣接因子から `lbl` への提案信念をプロットし（ベイズ木の表現は無視）、参照のために新しい積近似を表示します。線形および円形の信念積はタプルとして返されます。
