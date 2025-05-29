```julia
struct TriUpper{D} <: TriMatrices.TriLayout{D}
```

行列の上三角部分が格納され、対角線の下の値はゼロです。
