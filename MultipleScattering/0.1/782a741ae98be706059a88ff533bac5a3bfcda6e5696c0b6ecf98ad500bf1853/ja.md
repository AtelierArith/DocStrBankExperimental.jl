```
random_particles(particle_medium, particle_shapes::Vector{Shape}, region_shape, volume_fraction::Number;
    seed=Random.make_seed())
random_particles(particle_medium, particle_shape::Shape, region_shape, volume_fraction::Number;
    seed=Random.make_seed())
random_particles(particle_medium, particle_shape::Shape, region_shape, N::Integer;
    seed=Random.make_seed())
```

`N` 個のランダムな粒子を `region_shape` の内部に生成します（または `volume_fraction` で満たします）

出力を決定的にするためにシードを指定します。アルゴリズムは粒子を `region_shape` のバウンディングボックス内に均等にランダムに配置し、粒子が重なっている場合（外半径に基づく）やボックス内に完全に収まっていない場合は粒子を破棄します。

`particle_shapes::Vector{Shape}` を渡すと、各要素が同じ確率で発生することを前提とします。同じ形状を繰り返すと、それがより頻繁に配置されることになります。
