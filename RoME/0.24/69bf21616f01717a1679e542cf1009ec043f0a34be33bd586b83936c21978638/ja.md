```julia
generateGraph_Helix2DSlew!(; ...)
generateGraph_Helix2DSlew!(
    numposes;
    slew_x,
    slew_y,
    spine_t,
    kwargs...
)

```

標準的なスルー付きヘリックスグラフを生成します（平らにしたスリンキーのようなもの）。

ノート

  * `slew_x` と `slew_y` を使用して、一定の速度で異なる方向に「スリンキー」を引き出します。
  * 詳細については、一般化されたヘリックスジェネレーターを参照してください。
  * デフォルトは、x方向にスルーし、ヘリックスの連続ループ間で複数の軌道交差を持つように選択されています。

関連

[`generateGraph_Helix2D!`](@ref), [`generateGraph_Helix2DSpiral!`](@ref)
