```
StepsizeCallback(; cfl::Real)
```

CFL条件に従って時間ステップサイズを設定します。時間積分法が自動適応でない場合に適用されます。

現在の実装は、シミュレーション中に一定の時間ステップサイズを選択する最も単純なCFL条件の形式を使用しています。したがって、ステップサイズはシミュレーションの開始時に一度だけ適用されます。

ステップサイズ$\Delta t$は最小値として選択されます。

$$
    \Delta t = \min(\Delta t_\eta, \Delta t_a, \Delta t_c),
$$

ここで、

$$
    \Delta t_\eta = 0.125 \, h^2 / \eta, \quad \Delta t_a = 0.25 \sqrt{h / \lVert g \rVert},
    \quad \Delta t_c = \text{CFL} \, h / c,
$$

$$
\nu = \alpha h c / (2n + 4)
$$

、ここで$\alpha$は粘性のパラメータ、$n$は次元の数です。

!!! warning "実験的実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

[Antuono2012](@cite), [Adami2012](@cite), [Sun2017](@cite), [Antuono2015](@cite)
