```
MultiLens([castout,] lenses::Tuple)
MultiLens([castout,] lenses::NamedTuple)
```

# 例

```jldoctest
julia> using Setfield, Kaleido

julia> ml = MultiLens((
           (@lens _.x),
           (@lens _.y.z),
       ))
〈◻.x, ◻.y.z〉

julia> get((x=1, y=(z=2,)), ml)
(1, 2)

julia> set((x=1, y=(z=2,)), ml, ("x", "y.z"))
(x = "x", y = (z = "y.z",))

julia> ml = MultiLens((
           a = (@lens _.x),
           b = (@lens _.y.z),
       ))
〈◻.x, ◻.y.z〉

julia> get((x=1, y=(z=2,)), ml)
(a = 1, b = 2)

julia> set((x=1, y=(z=2,)), ml, (a=:x, b="y.z"))
(x = :x, y = (z = "y.z",))

julia> set((x=1, y=(z=2,)), ml, (b="y.z", a=:x))
(x = :x, y = (z = "y.z",))

julia> using StaticArrays

julia> ml = MultiLens(
           SVector,
           (
               (@lens _.x),
               (@lens _.y.z),
           )
       )
〈◻.x, ◻.y.z〉

julia> @assert get((x=1, y=(z=2,)), ml) === SVector(1, 2)
```
