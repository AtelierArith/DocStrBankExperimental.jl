```
random_normal_translation!(sys::System; shift_size=oneunit(eltype(eltype(sys.coords))),
                           rng=Random.default_rng())
```

ランダムに選択された原子の座標をランダムに移動させます [`System`](@ref) の中で。

この移動は、標準正規分布から選ばれた方向と長さを使用して生成されます。すなわち、平均0、標準偏差1のもので、`shift_size`によってスケーリングされ、適切な長さの単位を持つ必要があります。
