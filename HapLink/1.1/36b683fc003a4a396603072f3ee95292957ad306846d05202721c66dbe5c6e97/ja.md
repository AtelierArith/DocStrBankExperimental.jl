```
HaplotypeCall(
    haplotype::Haplotype{S,T}, reads::AbstractArray{Haplotype{S,T}}
) where {S<:BioSequence,T<:BioSymbol}
HaplotypeCall(
    haplotype::AbstractArray{Variation{S,T}}, reads::AbstractArray{Haplotype{S,T}}
) where {S<:BioSequence,T<:BioSymbol}
```

`haplotype`を`reads`内での連鎖不均衡を計算することによってハプロタイプを呼び出します。
