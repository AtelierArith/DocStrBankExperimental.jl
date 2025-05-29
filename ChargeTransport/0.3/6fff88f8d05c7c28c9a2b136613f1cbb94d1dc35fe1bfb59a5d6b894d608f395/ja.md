```julia
plot_solution(
    Plotter,
    ctsys,
    solution,
    title,
    label_solution;
    plotGridpoints
) -> Any

```

解法ベクトルをプロットするためのメソッド：静電ポテンシャル $\psi$ と電荷キャリア。ヘテロ接合のケースがテストされていますが、まだ多次元プロットは含まれていません。入力パラメータの一つはブール値の plotGridpoints で、ノードの位置を示すマーカーをプロットすることが可能です。
