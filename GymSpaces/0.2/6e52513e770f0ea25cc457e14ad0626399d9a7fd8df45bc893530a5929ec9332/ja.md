```
seed!(tuple_obj::TupleSpace, seeds...)
```

手動でシードを割り当てられた値に設定します。

# 例

julia> space = TupleSpace([Discrete(5), Discrete(10)]) . . .

julia> seed!(space, 42, 87) # TupleSpaceには2つのスペースしかないため

julia> sample(space) (4, 5)
