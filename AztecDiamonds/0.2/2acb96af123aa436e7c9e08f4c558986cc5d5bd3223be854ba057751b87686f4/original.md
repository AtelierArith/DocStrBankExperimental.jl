```
diamond(N::Int) -> Tiling{Matrix{AztecDiamonds.Edge}}
```

Generates a uniformally random order N diamond tiling.

```jldoctest
julia> using Random; Random.seed!(1);

julia> diamond(4)
Order-4 Tiling{Matrix{AztecDiamonds.Edge}}
      🬇🬋🬋🬃
    🬇🬋🬋🬃🬇🬋🬋🬃
  🬦🬓🬦🬓🬦🬓🬦🬓🬇🬋🬋🬃
🬦🬓🬉🬄🬉🬄🬉🬄🬉🬄🬇🬋🬋🬃🬦🬓
🬉🬄🬦🬓🬦🬓🬇🬋🬋🬃🬦🬓🬦🬓🬉🬄
  🬉🬄🬉🬄🬇🬋🬋🬃🬉🬄🬉🬄
    🬇🬋🬋🬃🬇🬋🬋🬃
      🬇🬋🬋🬃
```

See [`ka_diamond`](@ref) for a version that can take advantage of GPU acceleration. `ka_diamond(N, Array)` may also be faster for large N.

Ref [`Tiling`](@ref)
