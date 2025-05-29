```julia
struct MomentumMatrix{A<:(AbstractMatrix)}
```

モーメントマトリックスは、ジョイント速度ベクトルをモーメントにマッピングします。

これは、モーメントマトリックスが重心フレームで表現される必要がないという点で、重心モーメントマトリックス（Orin, Goswami, "Centroidal momentum matrix of a humanoid robot: Structure and properties."）のわずかな一般化です。
