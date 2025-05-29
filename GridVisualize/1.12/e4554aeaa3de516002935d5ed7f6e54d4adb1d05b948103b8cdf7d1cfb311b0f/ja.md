```julia
GridVisualizer(
;
    Plotter,
    kwargs...
) -> GridVisualize.GridVisualizer

```

グリッドビジュアライザーを作成します

Plotter: デフォルトは `default_plotter()` で、`PyPlot`、`Plots`、`VTKView`、`Makie` または `PlutoVista` に設定できます。このパターンにより、重いデフォルトパッケージの依存関係なしに、バックエンドをプロット関数にモジュールとして渡すことができます。

`layout` キーワード引数に応じて、2Dのサブプロットのグリッドが作成されます。さらに `...plot!` コマンドは、これらのサブプロットの1つにプロットします：

```julia
vis=GridVisualizer(Plotter=PyPlot, layout=(2,2)
...plot!(vis[1,2], ...)
```

`...plot` コマンドは、暗黙的にプロットコンテキストを作成します：

```julia
gridplot(grid, Plotter=PyPlot) 
```

は次のように等価です：

```julia
vis=GridVisualizer(Plotter=PyPlot, layout=(1,1))
gridplot!(vis,grid) 
reveal(vis)
```

すべてのプロットコマンドの戻り値は、Plotter に特有のものであることに注意してください。

GLMakie のインタラクティブモード切替キー (`,`) と VTKView (`*`) は、「ギャラリービュー」で全てのプロットを一度に表示し、「フォーカスビュー」で1つのプロットのみを表示する間で切り替えることを可能にします。

キーワード引数: [`available_kwargs`](@ref) を参照してください。
