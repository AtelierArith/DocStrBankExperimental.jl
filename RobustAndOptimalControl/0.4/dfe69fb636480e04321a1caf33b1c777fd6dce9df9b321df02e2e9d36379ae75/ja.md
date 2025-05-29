```
centers, radii = fit_complex_perturbations(P, w; relative=true, nominal=:mean)
```

各周波数 `w` に対して、モデルセット `P` に含まれるすべてのモデルを含む複素平面上の円をフィットさせます。`P` は `Particles` の係数を持つ `LTISystem` として表されます。注意すべきは、粒子の数が少ない場合、特に粒子が一様ではなく正規分布している場合、結果の半径が非常に不安定になる可能性があることです。

`realtive = true` の場合、`|(P - Pn)/Pn|` を含む円が返されます（乗法的/相対的不確実性）。`realtive = false` の場合、`|P - Pn|` を含む円が返されます（加法的不確実性）。

`nominal = :mean` の場合、`P` の平均が名目モデルとして使用されます。`nominal = :first` の場合、最初の粒子が使用されます。最初の粒子で名目値を設定するには `MonteCarloMeasurements.with_nominal` を参照してください。`nominal = :center` の場合、中点 `(pmaximum(ri)+pminimum(ri))/2` が使用されます。これは通常、最も小さな円を提供します。

円をプロットするには [`nyquistcircles`](@ref) も参照してください（`relative=false` の場合のみ）。
