```
POconfig{T, M, CBT<:ConfigBox, TH<:Union{T, NTuple{2, T}}, 
         OM} <: ConfigBox{T, POconfig, M}
```

The mutable container of parameter optimization configurations.

≡≡≡ Field(s) ≡≡≡

`method::Val{M}`: The method that defines the objective function (e.g., HF energy) for the  optimization. Available values of `M` from Quiqbox are :HFenergy, :DirectRHFenergy.

`config::CBT`: The configuration for the selected `method`. E.g., for `:HFenergy` it's  [`HFconfig`](@ref).

`target::T`: The target value of the objective function. The difference between the  last-step value and the target value will be used for convergence detection. If it's set to  `NaN`, the gradient of the latest step and the difference between the function values of  latest two steps are used instead.

`threshold::TH`: The error threshold/thresholds for the function value difference and  the gradient both/respectively to determine whether the optimization iteration has  converged. When it's (or either of them) set to `NaN`, there will be no corresponding  convergence detection, and when `target` is not `NaN`, the threshold for the gradient won't  be used because the gradient won't be part of the convergence criteria.

`maxStep::Int`: Maximum iteration steps allowed regardless if the iteration converges.

`optimizer::F`: Applied parameter optimizer. The default setting is [`GDconfig`](@ref)`()`.  To use a function implemented by the user as the optimizer, it should have the following  function signature: 

```
optimizer(f::Function, gf::Function, x0::Vector{T}) where {T} -> Function
```

where `f` is the objective function to be minimized, `gf` is a function that returns  both the gradient and the returned value of `f` given the input value as a vector. `x0` is  the initial input value. The output of `optimizer`, if we name it `optimize!`, should have  the corresponding function signature: 

```
optimize!(x::Vector{T}, gx::Vector{T}, fx::T) where {T}
```

where `x`, `gx`, `fx` are the input value, the gradient, and the returned value of `f`  respectively at one step. In other words, `(gx, fx) == (gx, f(x)) == gf(x)`. After  accepting those arguments, `optimizer` should update (i.e. mutate the elements of) `x` so  that f(x) will have lower returned value.

`saveTrace::NTuple{4, Bool}`: Determine whether saving (by pushing) the intermediate  information from all the iterations steps to the output of `optimizeParams!`. The types of relevant information are:

| Sequence |             Corresponding Information              |
|:--------:|:--------------------------------------------------:|
|    1     |        function value of the applied method        |
|    2     |                 parameter value(s)                 |
|    3     | function gradient with respect to the parameter(s) |
|    4     |       complete output of the applied method        |

≡≡≡ Initialization Method(s) ≡≡≡

```
POconfig(;method::Union{Val{M}, Symbol}=HFenergy, 
          config::ConfigBox=Quiqbox.defaultOFconfigs[method], 
          target::T=NaN, 
          threshold::Union{T, NTuple{2, T}}=(5.0e-8, 5.0e-5), 
          maxStep::Int=200, 
          optimizer::Function=GDconfig()) where 
        {T, M} -> 
POconfig{T, M}
```

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> POconfig();

julia> POconfig(maxStep=100);
```
