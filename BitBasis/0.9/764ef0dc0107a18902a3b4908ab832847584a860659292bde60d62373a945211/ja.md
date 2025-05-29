```
ismatch(index::Integer, mask::Integer, target::Integer) -> Bool
```

`mask`によってマスクされた位置のビットが`1`である場合、それが`target`と等しい場合は`true`を返します。

## 例

```julia
julia> n = 0b11001; mask = 0b10100; target = 0b10000;

julia> ismatch(n, mask, target)
true
```
