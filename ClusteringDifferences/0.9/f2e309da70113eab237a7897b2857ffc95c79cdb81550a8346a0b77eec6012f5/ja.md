```
kmeans(X::AbstractMatrix{<:Real}, μ::AbstractMatrix{<:Real}; <keyword arguments>)
```

[`kmeans`](@ref)と同様ですが、`X`のサイズに応じて`r`と`c`を自動的に生成します。
