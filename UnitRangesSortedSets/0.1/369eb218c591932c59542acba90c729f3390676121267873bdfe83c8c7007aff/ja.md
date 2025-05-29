ソートされた `UnitRange` のセット。昇順にソートされ、どの範囲も他の範囲と重複しません。

```julia
mutable struct UnitRangesSortedSet{K,TU} <: AbstractSet{TU}
    "最後に使用された範囲のインデックス。"
    lastusedrangeindex::IntSemiToken
    "範囲のストレージ：Dictのキーは`first(range)`で、Dictの値は`last(range)`です。"
    ranges::SortedDict{K,K,FOrd}
end
```

範囲は `SortedDict` に `first` をキー、`last` を値として格納されます。

`UnitRangesSortedSet` は標準の `Set` のように作成できます：

```julia
    UnitRangesSortedSet(somecontainer)
```

例えば

```julia
julia> using UnitRangesSortedSets

julia> UnitRangesSortedSet((1, 2, 4))
UnitRangesSortedSet{Int64} with 2 elements:
  1:2
  4:4

julia> UnitRangesSortedSet(('a':'z', 'α':'ω'))
UnitRangesSortedSet{Char} with 2 elements:
  'a':'z'
  'α':'ω'

julia> Random.seed!(1234);

julia> UnitRangesSortedSet(rand(1:20, 10))
UnitRangesSortedSet{Int64} with 6 elements:
   5:5
   7:8
  10:11
  15:16
  18:18
  20:20
```

または `push!` を使って：

```julia
julia> urs = UnitRangesSortedSet{Int}()
UnitRangesSortedSet{Int64}()

julia> push!(urs, 1)
UnitRangesSortedSet{Int64} with 1 element:
  1:1

julia> push!(urs, 2)
UnitRangesSortedSet{Int64} with 1 element:
  1:2

julia> push!(urs, 10:12)
UnitRangesSortedSet{Int64} with 2 elements:
   1:2
  10:12
```

範囲のセットを反復処理する：

```julia
julia> for r in urs @show(r) end
r = 1:2
r = 10:12

julia> for r in urs, i in r @show(i) end
i = 1
i = 2
i = 10
i = 11
i = 12

julia> for i in Iterators.flatten(urs) @show(i) end
i = 1
i = 2
i = 10
i = 11
i = 12

julia> collect(urs)
2-element Vector{UnitRange{Int64}}:
 1:2
 10:12
```

要素と範囲を削除する：

```julia
julia> delete!(urs, 10:11)
UnitRangesSortedSet{Int64} with 2 elements:
   1:2
  12:12

julia> delete!(urs, 1)
UnitRangesSortedSet{Int64} with 2 elements:
   2:2
  12:12
```

注意：`Char` の場合、`oneunit(UInt8)` ステップを持つ `StepRange{Char,UInt8}` が作成されます。
