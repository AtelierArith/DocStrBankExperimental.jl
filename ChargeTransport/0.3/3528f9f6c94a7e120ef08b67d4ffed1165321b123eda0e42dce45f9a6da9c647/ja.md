```julia
plot_energies(
    Plotter,
    ctsys,
    solution,
    title,
    label_energy;
    plotGridpoints
) -> Any

```

このメソッドを使用すると、エネルギーをプロットすることができます。

$$
E_\alpha - q \psi \quad \text{空間に関して。}
$$

ヘテロ接合のケースがテストされていますが、まだ多次元プロットは含まれていません。

入力パラメータの1つはブール値のplotGridpointsで、ノードがどこに位置しているかを示すマーカーをプロットすることができます。
