`interval(P,f::Function,a)` `interval(P,f::Function,a,g::Function,b)`

は、`P`によって与えられる`Poset`または`CPoset`内の区間を返します。関数`f`は比較関数の一つでなければなりません `≤, <, ≥, >`。最初の形式では、比較関数に応じて`a`の上または下の区間を返します；`a`は`P`の要素であるか、`P`の要素のベクトルである場合があります；後者の場合、`a`の任意の要素の下（または上）にある要素の順序理想が返されます。第二の形式では、`interval(P,f,a)`と`interval(P,g,b)`の区間の交差を返します。

```julia-repl
julia> l=vec(collect(Iterators.product(1:2,1:2)))
4-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (2, 1)
 (1, 2)
 (2, 2)

julia> P=Poset((x,y)->all(map(<=,x,y)),l)
(1, 1)<(2, 1),(1, 2)<(2, 2)

julia> interval(P,≤,(1,2)) # (1,2)の下にある要素
2-element Vector{Tuple{Int64, Int64}}:
 (1, 1)
 (1, 2)

julia> interval(P,≥,(1,2)) # (1,2)の上にある要素
2-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (2, 2)

julia> interval(P,<,(1,2)) # (1,2)の厳密に下にある要素
1-element Vector{Tuple{Int64, Int64}}:
 (1, 1)

julia> interval(P,≥,(2,1),≤,(2,2)) # (2,1)と(2,2)の間にある要素
2-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (2, 2)

julia> interval(P,>,(1,1),<,(2,2)) # 厳密に間にある要素
2-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (1, 2)
julia> interval(P.C,>,1,<,4) # インデックスに関して
2-element Vector{Int64}:
 2
 3
```
