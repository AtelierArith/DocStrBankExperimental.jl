```
AzimuthalCosine(s::NTuple{N,T}, ξ::NTuple{N, T}) where {N, T}
```

コサイン展開の順序 `N` によって与えられる方位プロファイル。展開は次のように与えられます。

```
    1 - ∑ₙ sₙcos(nϕ - ξₙ)
```

## ノート

これは通常、一般的なリングテンプレートを作成するために放射プロファイルと組み合わされます。

```julia-repl
julia> rad = RadialDblPower(3.0, 3.0)
julia> azi = AzimuthalCosine((0.5, 0.2), (0.0, π/4)) # デフォルトは Float64
julia> t = RingTemplate(rad, azi)
```

## 引数

  * `s` : 方位の明るさのコサイン展開の `N` 次の振幅
  * `ξs`: 方位の明るさのコサイン展開の `N` 次の位相
