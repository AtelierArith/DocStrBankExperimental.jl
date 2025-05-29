```
random_uniform_translation!(sys::System; shift_size=oneunit(eltype(eltype(sys.coords))),
                            rng=Random.default_rng())
```

ランダムに選択された原子の座標をランダムに移動させます [`System`](@ref) の中で。

移動は、均等に選択された方向と、範囲 [0, 1) で均等に選択された長さを使用して生成され、`shift_size` によって適切な長さの単位でスケーリングされます。
