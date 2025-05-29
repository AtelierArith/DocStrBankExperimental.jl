```
evaluate!(buffer::AbstractArray{T,N}, sampling, al; dim=1) where {T,N}
```

[`evaluate`](@ref)と同様ですが、結果を`buffer`に書き込みます。大きな一時配列を内部で割り当てないように、dim = 1またはNを使用してください。
