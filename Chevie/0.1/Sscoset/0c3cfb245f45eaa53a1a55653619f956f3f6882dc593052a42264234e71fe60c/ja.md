`quasi_isolated_reps(WF::Spets,p=0)`

`WF` は、コクセター余剰を表す代数的余剰 `𝐆 ⋅σ` を表すコクセター余剰である必要があります。ここで、`𝐆` は連結可解群（`W=Group(WF)` で表される）であり、`σ` は `WF` によって定義された `𝐆` の準中心自己同型です。この関数は、`tσ` がこのリストを走るとき、`𝐆 ⋅σ` の準孤立準単純要素の共役類の代表であるような `𝐆` の半単純要素のリストを返します（要素 `tσ∈ 𝐓 ⋅σ` は、`C_𝐆  (tσ)` のウェイグループが `W^σ` の任意の適切な部分放物群に含まれない場合、準孤立です）。第二の引数 `p` が与えられた場合、特性 `p` に存在する代表のみをリストします。

```julia-repl
julia> WF=rootdatum("2E6sc")
²E₆sc

julia> quasi_isolated_reps(WF)
5-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,-1,ζ₄,1,ζ₄,1>
 <1,1,1,-1,1,1>
 <1,ζ₃²,1,ζ₃,1,1>
 <1,ζ₄³,1,-1,1,1>

julia> quasi_isolated_reps(WF,2)
2-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,ζ₃²,1,ζ₃,1,1>

julia> quasi_isolated_reps(WF,3)
4-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,-1,ζ₄,1,ζ₄,1>
 <1,1,1,-1,1,1>
 <1,ζ₄³,1,-1,1,1>
```
