*(a::T, b::Union{T, AbstractString, AbstractChar}...) where {T <: AbstractPath} -> T

パス、文字列、および/または文字を連結し、新しいパスを生成します。これは、パスや他の文字列の文字列表現を連結し、その後新しいパスを構築することに相当します。

# 例

```jldoctest
julia> p"foo" * "bar"
p"foobar"
```
