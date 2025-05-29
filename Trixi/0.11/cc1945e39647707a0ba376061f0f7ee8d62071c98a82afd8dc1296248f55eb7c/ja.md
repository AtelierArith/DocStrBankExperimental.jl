```
VolumeIntegralUpwind(splitting)
```

有限差分部分和（FDSBP）ソルバー用の専門的な体積積分。SummationByPartsOperators.jlに実装されたMattsson（2017）の上流SBP演算子と一緒に使用できます。`splitting`は離散化を制御します。

他にも[`splitting_steger_warming`](@ref)、[`splitting_lax_friedrichs`](@ref)、[`splitting_vanleer_haenel`](@ref)を参照してください。

## 参考文献

  * Mattsson (2017) 対角ノルム上流SBP演算子 [doi: 10.1016/j.jcp.2017.01.042](https://doi.org/10.1016/j.jcp.2017.01.042)

!!! warning "実験的実装（上流SBP）"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

