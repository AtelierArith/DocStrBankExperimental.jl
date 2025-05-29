```
FroehlichPolaron(address::OccupationNumberFS{M}; kwargs...) <: AbstractHamiltonian
```

1D格子のためのFroehlichポラロンハミルトニアンは次のように与えられます。

$$
H = (p̂_f - p)^2/m + ωN̂ - v Σₖ(âₖ^† + â₋ₖ)
$$

ここで、$p$は全運動量、$p̂_f = Σ_k k âₖ^† âₖ$はボソンの運動量演算子であり、$k$は間隔$2π/l$の運動量格子の一部です。$N̂$はボソンの数演算子です。

# キーワード引数

  * `p=0.0`: 全運動量$p$。
  * `v=1.0`: 結合定数$v$。
  * `mass=1.0`: 粒子の質量$m$。
  * `omega=1.0`: フォノンの振動周波数$ω$。
  * `l=1.0`: 実空間における箱のサイズ$l$。運動量格子のスケールパラメータを提供します。
  * `momentum_cutoff=nothing`: アドレスに許可される最大ボソン運動量。
  * `mode_cutoff`: 各運動量モードにおけるボソンの最大数。デフォルトではアドレスタイプ[`OccupationNumberFS`](@ref)がサポートする最大値になります。

# 例

```jldoctest
julia> fs = OccupationNumberFS(0,0,0)
OccupationNumberFS{3, UInt8}(0, 0, 0)

julia> ham = FroehlichPolaron(fs; v=0.5)
FroehlichPolaron(fs"|0 0 0⟩{8}"; v=0.5, mass=1.0, omega=1.0, l=1.0, p=0.0, mode_cutoff=255)

julia> dimension(ham)
16777216

julia> dimension(FroehlichPolaron(fs; v=0.5, mode_cutoff=5))
216
```

他にも[`OccupationNumberFS`](@ref)、[`dimension`](@ref)、[`AbstractHamiltonian`](@ref)を参照してください。
