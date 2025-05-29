`conjcat(b[,F];ss=Val(:sc))`

は、必要なタイプの `b` のサミットセットの共役カテゴリを返します。

  * デフォルトでは、`b` のスライディング回路のカテゴリを計算します。
  * `ss==Val(:ss)` の場合、スーパーサミットセットを計算します。
  * `ss==Val(:cyc)` の場合、循環共役カテゴリを計算します。
  * `ss==Val(:inf)` の場合、`b` と同じ `Inf` を持つすべての共役要素のカテゴリを計算します。

引数 `F` が与えられた場合、それは `b.M.W` に付随する反射コセットのフロベニウスである必要があります。すると、`F`-共役カテゴリが返されます。

```julia-repl
julia> W=coxgroup(:A,4)
A₄

julia> w=BraidMonoid(W)(4,3,3,2,1)
43.321

julia> C=conjcat(w)
category with 2 objects and 4 generating maps

julia> C.obj # the (sliding circuits) summit set
2-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 32143
 21324
```

```julia-rep1
julia> xprint(C;graph=true)   # show the conjugations among the summit set
category with 2 objects and 4 generating maps
     32143      21343      21324      13214
32143────→ 32143────→ 21324────→ 21324────→ 32143
```

```julia-repl
julia> conjcat(w;ss=Val(:ss)).obj # the super summit set
4-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 32143
 13243
 21432
 21324
```
