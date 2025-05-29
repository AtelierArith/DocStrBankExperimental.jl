```
MinHashSketch
```

反復可能なオブジェクトのN個の最小ハッシュを保持します。`MinHasher`から構築します。

# 例

```jldoctest
julia> x = MinHashSketch(update!(MinHasher(10), 1:1000))
MinHashSketch:
 hashes:  10 / 10
 maxhash: 0x0214ce7a1c004d40

julia> length(x)
10
```
