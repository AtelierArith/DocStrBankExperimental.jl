```julia
struct TriSymmetric{D} <: TriMatrices.TriLayout{D}
```

行列は対角線に沿って対称であり、非対角エントリのペアごとに1つの値が保存されます。
