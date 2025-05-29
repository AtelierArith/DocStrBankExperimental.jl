```
weight(x::Real) -> Int
```

`x`をバイナリベクトルとして考えたときのハミング重み。`count_ones(x)`と同様に、`x`のビット表現における`1`の数をカウントしますが、必ずしも「ベアメタル」レベルではありません。例えば、`count_ones(big(-1))`はエラーになりますが、`weight(big(-1)) == Bits.INF`、すなわち`BigInt`は2の補数算術を用いた任意の大きなビットフィールドと見なされます。

# 例

```jldoctest
julia> weight(123)
6

julia> count(bits(123))
6
```
