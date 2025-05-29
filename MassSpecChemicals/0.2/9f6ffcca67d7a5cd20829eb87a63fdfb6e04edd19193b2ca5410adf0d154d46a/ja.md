```
AdductIon{S <: AbstractChemical, T <: AbstractAdduct} <: AbstractAdductIon{S, T}
```

質量分析におけるアダクトイオンの形成。

# フィールド

  * `core`: イオン化される元の化学物質。
  * `adduct`: イオンのアダクト。

# コンストラクタ

  * `AdductIon(name::AbstractString, a::AbstractString; kwargs...)` -> `AdductIon(parse_chemical(name; kwargs...), parse_adduct(a))`
  * `AdductIon(::Type{S}, name::AbstractString, a::AbstractString; kwargs...)` -> `AdductIon(parse_chemical(S, name; kwargs...), parse_adduct(a))`
  * `AdductIon(cc::AbstractChemical, a::AbstractString)` -> `AdductIon(cc, parse_adduct(a))`
  * `AdductIon(name::AbstractString, a::AbstractAdduct; kwargs...)` -> `AdductIon(parse_chemical(name; kwargs...), a)`
  * `AdductIon(::Type{S}, name::AbstractString, a::AbstractAdduct; kwargs...)` -> `AdductIon(parse_chemical(S, name; kwargs...), a)`
