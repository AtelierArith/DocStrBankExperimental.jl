`coxeter_symmetric_group(n::Integer)` または `coxeter_symmetric_group(m:n)` または `coxsym(n)` または `coxsym(m:n)`

文字 `1:n` の上の対称群（または `m≤n` が与えられた場合は、文字 `m:n` の上の対称群）をコクセター群として表現します。コクセター生成子は `Perm(i,i+1)` で、`i` は `m:n-1` の範囲です。

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> gens(W)
2-element Vector{Perm{Int16}}:
 (1,2)
 (2,3)

julia> e=elements(W)
6-element Vector{Perm{Int16}}:
 ()
 (1,2)
 (2,3)
 (1,3,2)
 (1,2,3)
 (1,3)

julia> length.(Ref(W),e) # 要素の生成子における長さ
6-element Vector{Int64}:
 0
 1
 1
 2
 2
 3
```
