`quasi_isolated_reps(W,p=0)`

`W` は、特性 0 の代数閉体上の代数群 𝐆 に対応するウィール群である必要があります。この関数は、準孤立半単純要素の 𝐆-軌道の代表である 𝐆 の半単純要素のリストを返します。これは、[Bonnafe2005](biblio.htm#Bon05) に示されたアルゴリズムに従います。第二の引数 `p` が与えられた場合、特性 `p` に存在する準孤立要素の代表を返します。

```julia-repl
julia> W=coxgroup(:E,6);l=quasi_isolated_reps(W)
5-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,-1,1,1,1,1>
 <1,1,1,ζ₃,1,1>
 <ζ₃,1,1,1,1,ζ₃>
 <1,ζ₆,ζ₆,1,ζ₆,1>

julia> map(s->isisolated(W,s),l)
5-element Vector{Bool}:
 1
 1
 1
 0
 0

julia> W=rootdatum(:E6sc);l=quasi_isolated_reps(W)
7-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <-1,1,1,-1,1,-1>
 <ζ₃,1,ζ₃²,1,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃,1,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃,1,ζ₃²,ζ₃>
 <ζ₆⁵,1,ζ₃²,1,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃,1,ζ₃²,ζ₆⁵>

julia> map(s->isisolated(W,s),l)
7-element Vector{Bool}:
 1
 1
 1
 1
 1
 1
 1

julia> Semisimple.quasi_isolated_reps(W,3)
2-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <-1,1,1,-1,1,-1>
```
