```
fasthash(s::SmallBitSet [, h0::UInt]) -> UInt
```

`s` のハッシュを返します。これは高速に計算でき、すべての `SmallBitSet` に対して一貫性がありますが、集合に使用される `hash` とは互換性がありません。

関連情報: `Base.hash`.

# 例

```jldoctest
julia> s = SmallBitSet(1:3);

julia> fasthash(s)
0x828a4cc485149963

julia> fasthash(s) == hash(s)
false

julia> t = SmallBitSet{UInt16}(s);

julia> fasthash(s) == fasthash(t)
true
```
