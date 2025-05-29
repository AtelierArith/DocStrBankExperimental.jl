```
abstract type IntervalRelation <: GeometricalRelation end
```

区間二項関係のための抽象型。1983年にアレンによって最初に定義された[区間代数](https://en.wikipedia.org/wiki/Allen%27s_interval_algebra)は、区間間の12の方向関係と同一性（すなわち、`identityrel`）を含みます。

12の関係は、6つの関係`after`、`later`、`begins`、`ends`、`during`、`overlaps`とその逆です。

参照区間`(x−y)`を考えると、各関係を通じてアクセス可能な世界`(z−t)`の例を提供することで、6つの基本関係をグラフィカルに表現できます：

| Relation | Full name          |   Property    |     Graphical Representation w.r.t (x−y)     |
|:-------- |:------------------ |:-------------:|:--------------------------------------------:|
|          |                    |               | `_____x___________________y________________` |
|          |                    |               | `_____∣−−−−−−−−−−−−−−−−−−−∣________________` |
|          |                    |               | `_____.___________________.________________` |
|          |                    |               | `_____.___________________z________t_______` |
| A        | After (or meets)   |     y = z     | `_____.___________________∣−−−−−−−−∣_______` |
|          |                    |               | `_____.___________________.________________` |
|          |                    |               | `_____.___________________.___z_________t__` |
| L        | Later              |     y < z     | `_____.___________________.___∣−−−−−−−−−∣__` |
|          |                    |               | `_____.___________________.________________` |
|          |                    |               | `_____z_____t_____________.________________` |
| B        | Begins (or starts) | x = z, t < y  | `_____∣−−−−−∣_____________.________________` |
|          |                    |               | `_____.___________________.________________` |
|          |                    |               | `_____._____________z_____t________________` |
| E        | Ends (or finishes) | y = t, x < z  | `_____._____________∣−−−−−∣________________` |
|          |                    |               | `_____.___________________.________________` |
|          |                    |               | `_____.___z________t______.________________` |
| D        | During             | x < z, t < y  | `_____.___∣−−−−−−−−∣______.________________` |
|          |                    |               | `_____.___________________.________________` |
|          |                    |               | `_____.___________z_______.____t___________` |
| O        | Overlaps           | x < z < y < t | `_____.___________∣−−−−−−−−−−−−∣___________` |

粗い関係は、これら12の関係の和によって定義できます。

# 例

```julia-repl
julia> IARelations
12-element Vector{IntervalRelation}:
 _IA_A()
 _IA_L()
 _IA_B()
 _IA_E()
 _IA_D()
 _IA_O()
 _IA_Ai()
 _IA_Li()
 _IA_Bi()
 _IA_Ei()
 _IA_Di()
 _IA_Oi()

julia> @assert SoleLogics._IA_L() == IA_L

julia> fr = SoleLogics.FullDimensionalFrame((10,),);

julia> collect(accessibles(fr, Interval(2,5), IA_L))
15-element Vector{Interval{Int64}}:
 (6−7)
 (6−8)
 (7−8)
 (6−9)
 (7−9)
 (8−9)
 (6−10)
 (7−10)
 (8−10)
 (9−10)
 (6−11)
 (7−11)
 (8−11)
 (9−11)
 (10−11)

julia> syntaxstring.(IARelations)
12-element Vector{String}:
 "A"
 "L"
 "B"
 "E"
 "D"
 "O"
 "A̅"
 "L̅"
 "B̅"
 "E̅"
 "D̅"
 "O̅"

julia> syntaxstring.(IA7Relations)
6-element Vector{String}:
 "AO"
 "L"
 "DBE"
 "A̅O̅"
 "L̅"
 "D̅B̅E̅"

julia> syntaxstring.(SoleLogics.IA3Relations)
3-element Vector{String}:
 "I"
 "L"
 "L̅"

```

[`IARelations`](@ref)、[`IA7Relations`](@ref)、[`IA3Relations`](@ref)、[`Interval`](@ref)、[`GeometricalRelation`](@ref)も参照してください。
