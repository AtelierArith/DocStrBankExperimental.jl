```
GlmSpeedCallback(; glm_scale=0.5, cfl, semi_indices=())
```

理想GLM-MHD方程、多成分GLM-MHD方程、および多イオンGLM-MHD方程のために、[`StepsizeCallback`](@ref)で計算された時間ステップに従って発散クリーニング波速度 `c_h` を更新します。 `cfl` 数は、時間ステップサイズ計算と同じ値に設定する必要があります。標準の[`StepsizeCallback`](@ref)と同様に、`cfl` は `Real` 数に設定するか、`Real` 数を返す時間 `t` の関数に設定できます。

`glm_scale` は、GLM波速度がMHD解の最も速い物理波よりも低くなることを保証し、したがって [0,1] の範囲内の値に設定する必要があります。 `glm_scale = 0` は発散クリーニングを無効にします。

結合された半離散化の場合、発散クリーニングを適用する `semi_index`、すなわち半離散化のインデックスを指定します。 [`SemidiscretizationCoupled`](@ref) も参照してください。注意: `SemidiscretizationCoupled` および関連するすべての機能は実験的と見なされ、いつでも変更される可能性があります。
