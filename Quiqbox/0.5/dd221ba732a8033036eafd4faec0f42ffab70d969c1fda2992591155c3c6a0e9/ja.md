```
copyBasis(b::GaussFunc, copyOutVal::Bool=true) -> GaussFunc

copyBasis(b::CompositeGTBasisFuncs, copyOutVal::Bool=true) -> CompositeGTBasisFuncs
```

入力基底のコピーを返します。`copyOutVal`が`true`に設定されている場合、`b`に格納されている[`ParamBox`](@ref)(s)の出力値のみがコピーされます。つまり、[`outValCopy`](@ref)が使用され、それ以外の場合は[`fullVarCopy`](@ref)が使用されます。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> f(x)=x^2; e = genExponent(3.0, f)
ParamBox{Float64, :α, …}{1}[𝛛][x_α]⟦→⟧[9.0]

julia> c = genContraction(2.0)
ParamBox{Float64, :d, …}{0}[∂][d]⟦=⟧[2.0]

julia> gf1 = GaussFunc(e, c);

julia> gf2 = copyBasis(gf1)
GaussFunc{Float64, …}{0, 0}[∂∂][{9.0, 2.0}]

julia> gf1.xpn() == gf2.xpn()
true

julia> (gf1.xpn[] |> gf1.xpn.map) == gf2.xpn[]
true
```
