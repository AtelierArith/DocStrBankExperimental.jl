```
index_to_dict(::Integer)
index_to_dict(::AbstractVector{Int})
index_to_dict(::UnitRange)
index_to_dict(::StepRange)
index_to_dict(::Colon)
index_to_dict(::ConcretizedSlice{T, Base.OneTo{I}}) where {T, I}
index_to_dict(::Tuple)
```

インデックス `i` を辞書表現に変換します。
