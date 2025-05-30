```
lowrank(L, D)::LDLᵀ
```

`alpha * L * D * L'` の遅延表現で、`alpha::Real` は初めは1であり、以下の関数をサポートします：

  * `+(::LDLᵀ, ::LDLᵀ)`
  * `*(::Real, ::LDLᵀ)`
  * `eltype(::LDLᵀ)` は `Base.promote_eltype(L, D)` を返します（`typeof(alpha)` と同じ）
  * `size`
  * `rank` は内側の次元の長さ、すなわち `size(L, 2)` を返します
  * `zero` はランク0の表現を返します
  * [`concatenate!`](@ref) （専門家用のみ）
  * [`compress!`](@ref) （専門家用のみ）

構造体を反復すると `alpha`、`L`、および `D` が得られます。必要に応じて [`compress!`](@ref) が呼び出されます。

便利のために、構造体は `Matrix` を介して行列に変換されることがあります。これはテストのためのみに使用することをお勧めします。
