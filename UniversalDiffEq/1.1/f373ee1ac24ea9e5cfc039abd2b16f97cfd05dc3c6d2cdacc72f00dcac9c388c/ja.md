```
plot_bifurcation_diagram(model::UDE, xvariable; N = 25, color_variable= nothing, conditional_variable = nothing, size= (600, 400))
```

この関数は、共変量 $X_t$ の関数としての状態変数 $y_t$ の平衡値のプロットを返します。引数 `xvariable` は、x軸にプロットされる共変量を決定します。追加の変数は、`conditional_variable` キーワード引数を指定することで別のパネルに視覚化することができ、`color_variable` 引数を使用してカラースキームで視覚化することもできます。

キーワード引数 `size` は、最終的なプロットの寸法を制御します。
