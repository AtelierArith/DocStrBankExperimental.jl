```
AutoEnzyme{M,A}
```

Struct used to select the [Enzyme.jl](https://github.com/EnzymeAD/Enzyme.jl) backend for automatic differentiation.

Defined by [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

# Constructors

```
AutoEnzyme(; mode::M=nothing, function_annotation::Type{A}=Nothing)
```

# Type parameters

  * `A` determines how the function `f` to differentiate is passed to Enzyme. It can be:

      * a subtype of `EnzymeCore.Annotation` (like `EnzymeCore.Const` or `EnzymeCore.Duplicated`) to enforce a given annotation
      * `Nothing` to simply pass `f` and let Enzyme choose the most appropriate annotation

# Fields

  * `mode::M` determines the autodiff mode (forward or reverse). It can be:

      * an object subtyping `EnzymeCore.Mode` (like `EnzymeCore.Forward` or `EnzymeCore.Reverse`) if a specific mode is required
      * `nothing` to choose the best mode automatically
