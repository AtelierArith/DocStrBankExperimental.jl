```
Space{D<:Domain, R}
```

`Fun` が定義されるさまざまな空間の抽象スーパタイプであり、ここで `R` はドメイン上の基底関数の型を表します。Space は `Domain` を型 `R` にマッピングします。

例えば、次のようになります。

  * `Chebyshev{Interval{Float64}} <: Space{Interval{Float64},Float64}`
  * `Laurent{PeriodicSegment{Float64}} <: Space{PeriodicSegment{Float64},ComplexF64}`
  * `Fourier{Circle{ComplexF64}} <: Space{Circle{ComplexF64},Float64}`

!!! note
    現在のところ、`Space` は係数に関する情報を含んでいません。

