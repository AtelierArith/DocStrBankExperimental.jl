```julia
linterp1s!(yq::StridedArray, x::StridedArray, y::StridedArray, xq; extrapolate=:Linear)
linterp1s!(yq::StridedArray, knot_index::StridedArray{Int}, x::StridedArray, y::StridedArray, xq::AbstractArray; extrapolate=:Linear)
```

`linterp1s`のインプレースバリアント。`x`をソートし、`y`を一致させるために置換した後、`xq`で補間を行い、結果を`yq`に格納します。

オプションの一時作業配列`knot_index = similar(xq, Int)`を提供することで、アロケーションを完全に排除できます。
