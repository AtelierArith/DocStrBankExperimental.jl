```
QubitSet
```

`OrderedSet`のようなオブジェクトで、[`Circuit`](@ref)、[`Instruction`](@ref)、または[`Result`](@ref)が作用するキュービットとその順序を表します。要素は`Int`または[`Qubit`](@ref)である可能性があります。

# 例

```jldoctest
julia> QubitSet(1, Qubit(0))
QubitSet with 2 elements:
  1
  Qubit(0)

julia> QubitSet([2, 1])
QubitSet with 2 elements:
  2
  1

julia> QubitSet()
QubitSet()

julia> QubitSet(QubitSet(5, 1))
QubitSet with 2 elements:
  5
  1
```
