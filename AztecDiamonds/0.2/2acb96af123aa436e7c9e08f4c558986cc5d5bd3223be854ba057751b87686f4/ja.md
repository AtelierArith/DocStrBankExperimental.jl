```
diamond(N::Int) -> Tiling{Matrix{AztecDiamonds.Edge}}
```

Nダイヤモンドタイルの均一にランダムな順序を生成します。

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

GPUアクセラレーションを活用できるバージョンについては[`ka_diamond`](@ref)を参照してください。大きなNの場合、`ka_diamond(N, Array)`の方が速いかもしれません。

Ref [`Tiling`](@ref)
