```
sinc_interpolate(arr, new_size [, normalize])
```

`arr`の`sinc`補間を新しい配列サイズ`new_size`で計算します。このメソッドはFFTに基づいており、したがって周期的境界と有限周波数サポートを暗黙的に仮定しています。`normalize=true`がデフォルトで、平均強度が同じになるように適切な係数で乗算します。

# 例

```jldoctest
julia> sinc_interpolate([1.0, 2.0, 3.0, 4.0], 8)
8-element Array{Float64,1}:
 1.0
 1.085786437626905
 2.0
 2.5
 3.0
 3.914213562373095
 4.0
 2.5

julia> sinc_interpolate([1.0  2.0; 3.0 4.0], (4,4))
4×4 Array{Float64,2}:
 1.0  1.5  2.0  1.5
 2.0  2.5  3.0  2.5
 3.0  3.5  4.0  3.5
 2.0  2.5  3.0  2.5
```
