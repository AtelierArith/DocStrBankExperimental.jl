```
PoissonEquation(h, ensemble) ::GainEquation
```

ポアソン方程式の構造体を返します。この方程式は $\nabla\cdot(p\nabla \phi) = - \tilde h$ であり、$p$ は確率密度、$\tilde h = h-\int h p dx$ です。コンテナには以下のフィールドが含まれています。

  * `:h':``h`` 自体
  * `:positions':``p`` からの独立同分布のサンプルで、行列として表現されます
  * `:H': サンプル点での``h``の評価
  * `:mean_H':`H'のサンプル平均
  * `:potential': サンプル点での``\phi``の評価
  * `:gain': サンプル点での``K=\nabla \phi``の評価

    solve!(eq::PoissonEquation, method::GainEstimationMethod)

フィールド `:gain' に適切な値を埋めます。フィールド`:H', `:mean_H', および`:potential' は再利用のために保存されます。

```
update!(eq::PoissonEquation, ensemble)
```

フィールド `:positions',`:H', および `:mean_H' を`ensemble' からの新しいサンプルに従って埋めます。

```
update!(eq::PoissonEquation)
```

フィールド `:H', および`:mean_H' を `:positions' と整合性を持たせるように更新します。
