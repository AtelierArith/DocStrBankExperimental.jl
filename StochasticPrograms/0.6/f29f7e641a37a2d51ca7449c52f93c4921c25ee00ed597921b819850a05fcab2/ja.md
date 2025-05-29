```
list_of_constraint_types(stochasticprogram::Stochasticprogram, stage::Integer)::Vector{Tuple{Type, Type}}
```

`(F, S)`の形式のタプルのリストを返します。ここで、`F`はJuMP関数型で、`S`はMOI集合型です。`all_constraints(stochasticprogram, stage, F, S)`が空でないリストを返すようなものです。
