`split_levis(WF,ζ::Root1=1[,ad])`

`WF` を反射群または反射コセットとします。`W` が反射群である場合、それは自明なコセット 'Spets(W)' として扱われます。*Levi* とは、`W₁F₁` の形をしたサブコセットであり、ここで `W₁` は `W` の*放物群*であり、`V` のいくつかの部分空間の中心化群であり、`F₁∈ WF` は `W₁` を正規化します。

`ζ` を単位根とします。`split_levis` は `W` の `ζ`-分割Leviの共役類の代表のリストを返します。`ζ`-分割Levi は、与えられた部分空間 `V_ζ` に対して `ζ` によって作用するすべての要素から形成される `WF` のサブコセットです。追加の引数 `ad` が与えられた場合、要素の共通 `ζ`-固有空間の次元が `ad` であるようなサブコセットのみを返します。これらの概念は意味を持ち、したがって任意の複素反射群に対して実装されています。

代数群の観点から、冗長群 `𝐆` の `F`-安定Levi部分群は、`ζ`-分割であるのは、中心の `Φ`-部分の中心化群である場合に限ります。ここで `Φ` は `ζ` を根とする巡回多項式です。`ζ=1` の場合、*分割* Levi の概念が得られ、これは `𝐆` の `F`-安定放物群のLevi部分群と同じです。

固有値 `ζ` は、整数 `d` を与えることによっても指定できます（この場合、`ζ=E(d)` を指定します）または分数 `a//b` を与えることによっても指定できます（この場合、`ζ=E(b,a)` を指定します）。省略された場合、`ζ` は `1` と見なされます。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> split_levis(W,4)
2-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 A₃
 A₃₍₎=Φ₂Φ₄

julia> W=spets(coxgroup(:D,4),Perm(1,2,4))
³D₄

julia> split_levis(W,3)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 ³D₄
 ³D₄₍₁₃₎=A₂Φ₃
 ³D₄₍₎=Φ₃²

julia> W=coxgroup(:E,8)
E₈

julia> split_levis(W,4,2)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 E₈₍₃₄₂₅₎=D₄₍₁₃₂₄₎Φ₄²
 E₈₍₅₇₂₃₎=(A₁A₁)×(A₁A₁)Φ₄²
 E₈₍₃₅₆₁₎=²(A₂A₂)₍₁₄₂₃₎Φ₄²

julia> split_levis(complex_reflection_group(5))
4-element Vector{Spets{PRSG{Cyc{Rational{Int64}}, Int16}}}:
 G₅
 G₅₍₁₎=G₃‚₁‚₁Φ₁
 G₅₍₂₎=G₃‚₁‚₁Φ₁
 G₅₍₎=Φ₁²
```
