```
ToEltype(T)
```

任意の `AbstractArrayItem` を `AbstractArrayItem{N, T}` に変換します。

`apply!` をサポートしています。

## 例

{cell=ToEltype}

```julia
using DataAugmentation

tfm = ToEltype(Float32)
item = ArrayItem(rand(Int, 10))
apply(tfm, item)
```
