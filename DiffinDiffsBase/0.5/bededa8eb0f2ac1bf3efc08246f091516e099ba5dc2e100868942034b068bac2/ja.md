```
notyettreated(e, ecut, c::ParallelCondition, s::ParallelStrength)
notyettreated(e, ecut=e; c=Unconditional(), s=Exact())
```

引数によって設定されたフィールドを持つ [`NotYetTreatedParallel`](@ref) を構築します。デフォルトでは、`c` は [`Unconditional()`](@ref) に、`s` は [`Exact()`](@ref) に設定されます。`@formula` を使用する際には、`notyettreated` のラッパーメソッドがこのメソッドを呼び出します。

# 例

```jldoctest; setup = :(using DiffinDiffsBase)
julia> notyettreated(5)
未処理のグループを持つ並行トレンド:
  未処理のグループ: 5
  処理済み: 5

julia> typeof(notyettreated(5))
NotYetTreatedParallel{Unconditional,Exact}

julia> notyettreated([-1, 5, 6], 5)
未処理のグループを持つ並行トレンド:
  未処理のグループ: -1, 5, 6
  処理済み: 5

julia> notyettreated([4, 5, 6], [4, 5, 6])
未処理のグループを持つ並行トレンド:
  未処理のグループ: 4, 5, 6
  処理済み: 4, 5, 6
```
