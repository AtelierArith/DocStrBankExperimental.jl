Tabloid(matrix::AbstractMatrix{<:Integer}, ordering::AbstractVector{<:Integer}=collect(1:maximum(matrix)))

与えられた順序で行列の行に対応するタブロイドを返します。行のエントリは順序に従ってソートされ、その後行は辞書式順序（タブロー順）で並べられます。

# 例

```jldoctest
julia> Tabloid([4 2 1; 3 1 4], [3,1,2,4])
[3 1 4; 1 2 4]
```

```jldoctest
julia> Tabloid([4 2 1; 3 1 4], [3,2,4,1])
[3 4 1; 2 4 1]
```
