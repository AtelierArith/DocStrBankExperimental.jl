演算子に対するスーパー演算子の象徴的な適用

```jldoctest
julia> @op A; @superop S;

julia> S*A
S[A]
```
