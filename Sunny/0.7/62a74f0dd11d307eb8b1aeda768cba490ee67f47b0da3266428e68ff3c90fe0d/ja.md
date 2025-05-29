```
intensities_static(swt::SpinWaveTheory, qpts; bounds=(-Inf, Inf), kernel=nothing, kT=0)
intensities_static(sc::SampledCorrelations, qpts; bounds=(-Inf, Inf), kT)
intensities_static(sc::SampledCorrelationsStatic, qpts)
```

[`intensities`](@ref)と同様ですが、エネルギーの範囲$ω$にわたって動的相関$\mathcal{S}(𝐪, ω)$を統合します。デフォルトでは、統合の`bounds`は$(-∞, ∞)$であり、瞬時（等時）相関を得ることができます。

[`SpinWaveTheory`](@ref)では、積分は離散バンドの合計として実現されます。代替計算方法には[`SpinWaveTheorySpiral`](@ref)と[`SpinWaveTheoryKPM`](@ref)があります。

[`SampledCorrelations`](@ref)の古典的動力学データも静的強度を計算するために使用できます。この場合、積分の範囲は利用可能な`energies`の有限グリッドになります。ここで、パラメータ`kT`は、[`intensities`](@ref)に記載されているように、励起の量子熱占有を考慮するために使用されます。

[`SampledCorrelationsStatic`](@ref)から計算された静的強度は動的に依存しません。代わりに、古典的ボルツマン分布からサンプリングされた瞬時相関が報告されます。
