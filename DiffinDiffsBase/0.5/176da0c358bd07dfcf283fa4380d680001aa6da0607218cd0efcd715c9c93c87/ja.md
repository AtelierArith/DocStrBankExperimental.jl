```
nevertreated(e, c::ParallelCondition, s::ParallelStrength)
nevertreated(e; c=Unconditional(), s=Exact())
```

引数によって設定されたフィールドを持つ [`NeverTreatedParallel`](@ref) を構築します。デフォルトでは、`c` は [`Unconditional()`](@ref) に、`s` は [`Exact()`](@ref) に設定されています。`@formula` を使用する際には、`nevertreated` のラッパーメソッドがこのメソッドを呼び出します。

# 例

```jldoctest; setup = :(using DiffinDiffsBase)
julia> nevertreated(-1)
任意の未処理グループとの平行トレンド:
  未処理グループ: -1

julia> typeof(nevertreated(-1))
NeverTreatedParallel{Unconditional,Exact}

julia> nevertreated([-1, 0])
任意の未処理グループとの平行トレンド:
  未処理グループ: -1, 0

julia> nevertreated([-1, 0]) == nevertreated(-1:0) == nevertreated(Set([-1, 0]))
true
```
