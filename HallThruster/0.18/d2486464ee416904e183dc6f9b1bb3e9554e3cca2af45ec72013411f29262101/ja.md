```julia
struct Species
```

特定の電荷状態を持つガスを表します。プラズマ内では、同じガスの異なるイオン化状態が共存する可能性があるため、これらを区別できる必要があります。

# フィールド

  * `element::HallThruster.Gas`: 種の基礎を形成するガス
  * `Z::Int64`: 種の電荷状態、すなわち Z = 1 は単一電荷の種を示します
  * `symbol::Symbol`: 種のシンボル、すなわち `Species(Xenon, 1)` の場合は `Symbol(Xe+)` です

```jldoctest;setup = :(using HallThruster: Xenon, Species)
julia> Species(Xenon, 0)
Xe

julia> Species(Xenon, 1)
Xe+

julia> Species(Xenon, 3)
Xe3+
```
