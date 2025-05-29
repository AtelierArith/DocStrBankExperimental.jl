```
abstract type RCCRelation <: GeometricalRelation end
```

[領域接続計算](https://en.wikipedia.org/wiki/Region_connection_calculus)からのトポロジカル二項関係。領域接続計算（RCC）は、アイデンティティ関係（すなわち、`identityrel`）と以下の7つの関係を含む8つのトポロジカル関係のセットであるRCC8で最も有名です。

  * 外部接続;
  * 部分的重なり;
  * 接線的適切部分;
  * 接線的適切部分の逆;
  * 非接線的適切部分;
  * 非接線的適切部分の逆。

参照区間 `(x−y)` を考えると、各関係を通じてアクセス可能な世界 `(z−t)` の例を提供することで、7つの関係をグラフィカルに表現できます。

| 関係    | 完全名        |                           (x−y) に関するグラフィカル表現 |
|:----- |:---------- | --------------------------------------------:|
|       |            | `___x___________________y__________________` |
|       |            | `___∣−−−−−−−−−−−−−−−−−−−∣__________________` |
|       |            | `___.___________________.__________________` |
|       |            | `___.___________________.__z________t______` |
| DC    | 切断された      | `___.___________________._∣−−−−−−−−∣_______` |
|       |            | `___.___________________.__________________` |
|       |            | `___.___________________z_________t________` |
| EC    | 外部接続       | `___.___________________∣−−−−−−−−−∣________` |
|       |            | `___.___________________.__________________` |
|       |            | `___.________________z_____t_______________` |
| PO    | 部分的重なり     | `___.________________∣−−−−−∣_______________` |
|       |            | `___.___________________.__________________` |
|       |            | `___._____________z_____t__________________` |
| TPP   | 接線的適切部分    | `___._____________∣−−−−−∣__________________` |
|       |            | `___.___________________.__________________` |
|       |            | `___z___________________._____t____________` |
| TPPi  | 接線的適切部分の逆  | `___∣−−−−−−−−−−−−−−−−−−−−−−−−−∣____________` |
|       |            | `___.___________________.__________________` |
|       |            | `___.___________z_______.__________________` |
| NTPP  | 非接線的適切部分   | `___.___________∣−−−−−∣_.__________________` |
|       |            | `___.___________________.__________________` |
|       |            | `_z_.___________________._t________________` |
| NTPPi | 非接線的適切部分の逆 | `_∣−−−−−−−−−−−−−−−−−−−−−−−∣________________` |

RCC8関係とInterval2Dのメソッドは、以下の合成ルールに従って1Dバージョンを組み合わせることで得られます。

|       | DC  | EC  | PO  | TPP | TPP | NTPP | NTPP | Id  |
|:----- |:--- |:--- |:--- |:--- |:--- |:---- |:---- |:--- |
| DC    | DC  | DC  | DC  | DC  | DC  | DC   | DC   | DC  |
| EC    | DC  | EC  | EC  | EC  | EC  | EC   | EC   | EC  |
| PO    | DC  | EC  | PO  | PO  | PO  | PO   | PO   | PO  |
| TPP   | DC  | EC  | PO  | TPP | PO  | TPP  | PO   | TPP |
| TPPi  | DC  | EC  | PO  | PO  | TPP | PO   | TPP  | TPP |
| NTPP  | DC  | EC  | PO  | TPP | PO  | NTPP | PO   | TPP |
| NTPPi | DC  | EC  | PO  | PO  | TPP | PO   | NTPP | TPP |
| Id    | DC  | EC  | PO  | TPP | TPP | TPP  | TPP  | Id  |

# 例

```julia-repl
julia> RCC8Relations
7-element Vector{RCCRelation}:
 _Topo_DC()
 _Topo_EC()
 _Topo_PO()
 _Topo_TPP()
 _Topo_TPPi()
 _Topo_NTPP()
 _Topo_NTPPi()

julia> @assert SoleLogics._Topo_DC() == Topo_DC

julia> fr = SoleLogics.FullDimensionalFrame((10,),);

julia> collect(accessibles(fr, Interval(4,8), Topo_DC))
6-element Vector{Interval{Int64}}:
 (9−10)
 (9−11)
 (10−11)
 (1−2)
 (1−3)
 (2−3)

julia> syntaxstring.(RCC8Relations)
7-element Vector{String}:
 "DC"
 "EC"
 "PO"
 "TPP"
 "T̅P̅P̅"
 "NTPP"
 "N̅T̅P̅P̅"

julia> RCC5Relations
4-element Vector{RCCRelation}:
 _Topo_DR()
 _Topo_PO()
 _Topo_PP()
 _Topo_PPi()
```

[`RCC8Relations`](@ref)、[`RCC5Relations`](@ref)、[`Interval`](@ref)、[`IntervalRelation`](@ref)、[`GeometricalRelation`](@ref)も参照してください。
