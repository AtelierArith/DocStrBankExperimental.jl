SPerm{T}(x::Integer...)where T<:Integer

`SPerm{T}`として符号付きサイクルを返します。例えば、`SPerm{Int8}(1,-2,-1,2)` と `SPerm({Int8}[-2,1])` は同じ符号付き置換を定義します。指定がない場合、`{T}` は `{Int16}` として取られます。
