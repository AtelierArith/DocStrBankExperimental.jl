```
number_density(s::Specie)
```

粒子の単位体積あたりの数を返します。これは、`N / V` によって正確に与えられ、ここで `V` はすべての粒子の起源を含む領域の体積です。一貫性のために、[`volume_fraction`](@ref) は `N * volume(s) / V` によって与えられます。
