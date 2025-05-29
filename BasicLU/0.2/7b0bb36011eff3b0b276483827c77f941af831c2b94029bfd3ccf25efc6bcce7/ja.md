```
L, U, p, q = getfactors(F::LUFactor) -> L::SparseMatrixCSC{Float64, Int64},
                                              U::SparseMatrixCSC{Float64, Int64},
                                              p::Vector{Int64},
                                              q::Vector{Int64}
```

新しい因子分解の後にLU因子を抽出します。`L`は単位下三角行列で、`U`は上三角行列であり、`p`と`q`は置換ベクトルで、行列`B`が因子分解されたときに（丸め誤差を無視すると）`B[p,q] = L * U`となります。
