```
normalize!(h::Histogram{T,N}, aux_weights::Array{T,N}...; mode::Symbol=:pdf) where {T<:AbstractFloat,N}
```

ヒストグラム `h` を正規化し、必要に応じて1つ以上の補助重み配列を適切にスケーリングします。詳細については `normalize` の説明を参照してください。`h` を返します。
