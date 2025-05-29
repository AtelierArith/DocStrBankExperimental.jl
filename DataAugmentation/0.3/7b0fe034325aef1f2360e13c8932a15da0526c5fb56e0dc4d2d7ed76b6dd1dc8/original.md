```
ToEltype(T)
```

Converts any `AbstractArrayItem` to an `AbstractArrayItem{N, T}`.

Supports `apply!`.

## Examples

{cell=ToEltype}

```julia
using DataAugmentation

tfm = ToEltype(Float32)
item = ArrayItem(rand(Int, 10))
apply(tfm, item)
```
