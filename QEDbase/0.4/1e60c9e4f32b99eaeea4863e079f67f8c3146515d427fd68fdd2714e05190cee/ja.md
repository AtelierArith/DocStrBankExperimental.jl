粒子が[`is_boson`](@ref)であり、$y$方向に偏光を持つことを示す具体的な型です。

```jldoctest
julia> using QEDbase

julia> PolY()
y-polarized
```

!!! note "座標軸"
    軸の概念、例えば$x$方向と$y$方向は、2つの直交する偏光方向を区別するためのものです。しかし、[`is_boson`](@ref)を持つ粒子の三次元運動量が座標系の$z$軸に整列している場合、偏光軸はそれぞれ$x$軸または$y$軸を定義します。


!!! info "エイリアス"
    `PolarizationY`の組み込みエイリアスがあります：

    ```jldoctest
    julia> using QEDbase

    julia> PolarizationY === PolY
    true
    ```

