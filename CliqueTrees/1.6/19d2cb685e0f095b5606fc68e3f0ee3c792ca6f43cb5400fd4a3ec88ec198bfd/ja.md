```
SinglyLinkedList{I, Head, Next} <: AbstractLinkedList{I}

SinglyLinkedList{I}(n::Integer)
```

異なる自然数の単方向リンクリスト。この型は[イテレーションインターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration)をサポートしています。

```jldoctest
julia> using CliqueTrees

julia> list = SinglyLinkedList{Int}(10)
SinglyLinkedList{Int64, Array{Int64, 0}, Vector{Int64}}:

julia> pushfirst!(list, 4, 5, 6, 7, 8, 9)
SinglyLinkedList{Int64, Array{Int64, 0}, Vector{Int64}}:
 4
 5
 6
 7
 8
 ⋮

julia> collect(list)
6-element Vector{Int64}:
 4
 5
 6
 7
 8
 9
```
