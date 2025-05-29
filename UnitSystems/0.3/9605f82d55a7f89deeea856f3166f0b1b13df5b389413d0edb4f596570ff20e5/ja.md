```Julia
wienfrequency(U::UnitSystem) = (𝟑+W₀(-𝟑*exp(-𝟑)))*boltzmann(U)/planck(U)
```

ウィーン周波数放射法則定数は、ランベルト `W₀` 評価に基づいています (Hz⋅K⁻¹)。

```Julia
julia> wienfrequency(Metric) # Hz⋅K⁻¹
5.87892575562598e10

julia> wienfrequency(SI2019) # Hz⋅K⁻¹
5.8789257576468254e10

julia> wienfrequency(Conventional) # Hz⋅K⁻¹
5.878925755625979e10

julia> wienfrequency(CODATA) # Hz⋅K⁻¹
5.87892376298804e10

julia> wienfrequency(English) # Hz⋅°R⁻¹
3.2660698642366558e10
```
