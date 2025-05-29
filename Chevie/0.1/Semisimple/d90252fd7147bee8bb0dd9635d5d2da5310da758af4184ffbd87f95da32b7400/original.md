`torsion_subgroup(S::SubTorus,n)`

This  function  returns  the  subgroup  of  semi-simple  elements  of order dividing `n` in the subtorus `S`.

```julia-repl
julia> G=rootdatum(:sl,4)
sl₄

julia> L=reflection_subgroup(G,[1,3])
A₃₍₁₃₎=A₁×A₁Φ₁

julia> C=algebraic_center(L)
(Z0 = SubTorus(A₃₍₁₃₎=A₁×A₁Φ₁,[1 2 1]), AZ = Group(SemisimpleElement{Root1}[<1,1,-1>]), descAZ = [[1, 2]], ZD = Group(SemisimpleElement{Root1}[<-1,1,1>, <1,1,-1>]))

julia> T=torsion_subgroup(C.Z0,3)
Group(SemisimpleElement{Root1}[<ζ₃,ζ₃²,ζ₃>])

julia> sort(elements(T))
3-element Vector{SemisimpleElement{Root1}}:
 <1,1,1>
 <ζ₃,ζ₃²,ζ₃>
 <ζ₃²,ζ₃,ζ₃²>
```
