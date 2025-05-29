```
enclose(A::AbstractMatrix{T}, b::AbstractVector{T}) where {T<:Interval}
```

区間線形システム $Ax=b$ の解の包絡を、[[HOR19]](@ref) のセクション 5.7.1 で説明されているアルゴリズムを使用して計算します。
