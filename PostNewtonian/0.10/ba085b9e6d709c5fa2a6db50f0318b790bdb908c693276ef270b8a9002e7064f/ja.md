```
uniform_in_phase(solution, saves_per_orbit)
```

位相における均一なステップに `solution` を補間します。

デフォルトでは、[`orbital_evolution`](@ref) によって返される `solution` は非常にまばらにサンプリングされる可能性があります — 波形のナイキスト限界を満たすには不十分です。波形が $\ell_{\mathrm{max}}$ に達する場合、$\exp\left(\pm i\, \ell_{\mathrm{max}}\, \Phi \right)$ よりもわずかに速く変化するモードがあります。周波数が一定であれば、これは軌道ごとに少なくとも $2\ell_{\mathrm{max}}$ サンプルを必要とします。安全係数を考慮すると、$4\ell_{\mathrm{max}}$ がかなり信頼性が高いようです。

[`orbital_evolution`](@ref) の `saves_per_orbit` および `saveat` 引数、ならびにその関数の結果の時間における補間機能も参照してください。
