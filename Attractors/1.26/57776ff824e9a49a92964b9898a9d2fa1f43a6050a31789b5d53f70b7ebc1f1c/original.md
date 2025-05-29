```
swap_dict_keys!(d::Dict, matching_map::Dict)
```

Swap the keys of a dictionary `d` given a `matching_map` which maps old keys to new keys. Also ensure that a swap can happen at most once, e.g., if input `d` has a key `4`, and `rmap = Dict(4 => 3, 3 => 2)`, then the key `4` will be transformed to `3` and not further to `2`.
