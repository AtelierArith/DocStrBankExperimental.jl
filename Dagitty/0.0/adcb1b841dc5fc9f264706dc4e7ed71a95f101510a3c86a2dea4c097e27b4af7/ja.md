```
DAGHasLoops
```

例外、DAG構築時にループが検出されたときにスローされます。

# 例

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :B, :B => :A)
ERROR: DAGHasLoops()
```
