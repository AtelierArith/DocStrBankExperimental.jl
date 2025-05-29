```
ParamBox{T, V, F<:Function} <: DifferentiableParameter{T, ParamBox}
```

Parameter container that can enable differentiation.

≡≡≡ Field(s) ≡≡≡

`data::Array{Pair{Array{T, 0}, Symbol}, 0}`: The container of the input variable data  in the form of a `Pair` of its value container and symbol) stored in the `ParamBox`. The  value of the input variable can be accessed by syntax `[]`; to modify it, for example for a  `pb::ParamBox{T}`, use the syntax `pb[] = newVal` where `newVal` is the new value that is  or can be converted into type `T`.

`map::Union{F,`[`DI`](@ref)`{F}}`: The mapping of the value of the input variable (i.e.  the input value) within the same domain (`.map(::T)->T`). The result (i.e., the value of  the output variable, or the "output value") can be accessed by syntax `()`.

`canDiff::Array{Bool, 0}`: Indicator of whether the output variable is "marked" as  differentiable with respect to the input variable in the differentiation process. In other  words, it determines whether the output variable represented by the `ParamBox` is treated  as a dependent variable or an independent variable.

`index::Array{Union{Int, Nothing}, 0}`: Additional index assigned to the `ParamBox`.

≡≡≡ Initialization Method(s) ≡≡≡

```
ParamBox(inVar::Union{T, Array{T, 0}}, outSym::Symbol=:undef, 
         inSym::Symbol=Symbol(IVsymSuffix, outSym); 
         index::Union{Int, Nothing}=nothing, canDiff::Bool=false) where {T} -> 
ParamBox{T, outSym, typeof(Quiqbox.itself)}

ParamBox(inVar::Union{T, Array{T, 0}}, outSym::Symbol, mapFunction::Function, 
         inSym::Symbol=Symbol(IVsymSuffix, outSym); 
         index::Union{Int, Nothing}=nothing, canDiff::Bool=true) where {T} -> 
ParamBox{T, outSym}
```

=== Positional argument(s) ===

`inVar::Union{T, Array{T, 0}}`: The value or the container of the input variable to be  stored. If the latter is the type of `data`, then it will directly used to construct  `.data[]` with without any copy.

`outSym::Symbol`: The symbol of the output variable represented by the constructed  `ParamBox`. It's equal to the type parameter `V` of the constructed `ParamBox`.

`inSym::Symbol`: The symbol of the input variable held by the constructed `ParamBox`.

`mapFunction::Function`: The mapping (`mapFunction(::T)->T`) of the input variable, which  will be assigned to the field `.map`. When `mapFunction` is not provided, `.map` is set to  [`itself`](@ref) that maps the input variable to an identical-valued output variable.

=== Keyword argument(s) ===

`index::Union{Int, Nothing}`: The index of the constructed `ParamBox`. It's should be left  with its default value unless the user plans to utilize the index of a `ParamBox` for  specific application other than differentiation.

`canDiff::Bool`: Determine whether the output variable is marked as "differentiable" with  respect to the input variable.

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> ParamBox(1.0)
ParamBox{Float64, :undef, …}{0}[∂][undef]⟦=⟧[1.0]

julia> ParamBox(1.0, :a)
ParamBox{Float64, :a, …}{0}[∂][a]⟦=⟧[1.0]

julia> ParamBox(1.0, :a, abs)
ParamBox{Float64, :a, …}{1}[𝛛][x_a]⟦→⟧[1.0]
```

**NOTE 1:** The markers "`[∂][IV]`" in the printed info indicate the differentiability and  the name (the symbol with an assigned index if applied) respectively of the independent  variable tied to the `ParamBox`. When the `ParamBox` is marked as non-differentiable,  "`[∂]`" is grey and `IV` corresponds to the name of the output variable; when the  `ParamBox` is  marked as differentiable, "`[∂]`" becomes a green "`[𝛛]`", and `IV`  corresponds to the name of the stored input variable.

**NOTE 2:** The output variable of a `ParamBox` is normally used to differentiate a  parameter functional (e.g., the Hartree–Fock energy). However, the derivative with respect  to the stored input variable can also be computed to when the `ParamBox` is marked as  differentiable.
