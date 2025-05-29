```
noise(n, noise::AbstractNoise)
```

位置 `n` でノイズ関数 `noise` を計算します。

## 例

```jldoctest
julia> sqn = SquirrelNoise5()
SquirrelNoise5(0x00000000)

julia> noise(5, sqn)
0x933e65af
```
