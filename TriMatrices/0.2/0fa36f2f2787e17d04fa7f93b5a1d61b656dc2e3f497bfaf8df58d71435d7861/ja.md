```julia
struct TriLower{D} <: TriMatrices.TriLayout{D}
```

行列の下三角部分が格納され、対角線の上の値はゼロです。
