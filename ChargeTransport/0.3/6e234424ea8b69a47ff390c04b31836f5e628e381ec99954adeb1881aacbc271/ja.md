```julia
plot_densities(
    Plotter,
    ctsys,
    solution,
    title,
    label_density;
    plotGridpoints
) -> Any

```

空間に依存した電荷キャリア密度を描画するプロットルーチンです。ヘテロ接合のケースがテストされていますが、まだ多次元プロットは含まれていません。入力パラメータの一つはブール値のplotGridpointsで、ノードの位置を示すマーカーをプロットすることが可能です。
