```
select(
    bibliography::DataStructures.OrderedDict{String,Entry},
    selection::Vector{String};
    complementary::Bool = false
    )
```

Select a part of a bibliography based on a given selection set of keys. If complementary is true, selection designates which entries will not be kept. By default, complementary is set to false.
