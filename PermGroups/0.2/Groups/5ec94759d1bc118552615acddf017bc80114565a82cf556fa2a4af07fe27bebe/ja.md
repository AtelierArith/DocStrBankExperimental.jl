`(G::Group)(i...)`

関数として使用されるグループは、`eachindex(gens(W))`の整数引数を取ります。これは、指定されたインデックスの生成器の積の要素を`G`として構築します。引数は負の値も取ることができ、その場合は対応する生成器の逆が使用されます。

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3))
Group((1,2),(1,2,3))

julia> G(2,1,-2) # returns gens(G)[2]*gens(G)[1]/gens(G)[2]
(1,3)
```
