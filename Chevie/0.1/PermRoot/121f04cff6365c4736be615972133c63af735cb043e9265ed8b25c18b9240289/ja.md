`invariants(W::ComplexReflectionGroup)`

は、`W` の反射表現 `V` における基本的な不変量を返します。つまり、`V` の双対の対称代数の代数的に独立な要素の集合を返し、これが `W`-不変な多項式関数を生成します。このような不変関数は関数として返されます：もし `e₁,…,eₙ` が `V` の基底であり、`f` がその関数であれば、`a₁e₁+…+aₙeₙ` における多項式関数の値は `f(a₁,…,aₙ)` を呼び出すことで得られます。この関数は分類に依存し、`W` の正確な反射表現に依存します。したがって、現時点では、不可約成分の反射表現が対応する不可約群のために Chevie によって提供されたのと同じカルタン行列を持つ場合にのみ実装されています。多項式は、行列としての群要素の自然な作用に対して不変です。つまり、もし `m==reflrep(W,w)` が `W` のある `w` に対して成り立つなら、不変な `f` は `f(a₁,…,aₙ)=f(v₁,…,vₙ)` を満たします。ここで、`[v₁,…,vₙ]=[a₁,…,aₙ]×m` です。この作用は、関数 `^` によって `Mvp` に実装されています。

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> @Mvp x,y,z

julia> i=invariants(W);

julia> map(f->f(x,y),i)
2-element Vector{Mvp{Int64, Int64}}:
 -2x²+2xy-2y²
 6x²y-6xy²

julia> W=complex_reflection_group(24)
G₂₄

julia> p=invariants(W)[1](x,y,z)
Mvp{Rational{Int64}}: (14//1)x⁴+(-12//1)x²y²+(-42//1)x²yz+(21//2)x²z²+(18//7)y⁴+(-6//1)y³z+(-9//2)y²z²+(-21//8)z⁴

julia> map(v->^(v,reflrep(W,1);vars=[:x,:y,:z]),(x,y,z))
((1//2)x+(3√-7/14)y, (-√-7/2)x+(-1//2)y, z)

julia> p^reflrep(W,1)-p
Mvp{Cyc{Rational{Int64}}}: 0
```
