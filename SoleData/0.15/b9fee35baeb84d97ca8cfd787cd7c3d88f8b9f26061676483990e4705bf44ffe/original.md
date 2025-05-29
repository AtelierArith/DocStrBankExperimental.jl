```
scalarlogiset(dataset, features; kwargs...)
```

Convert a dataset structure (with variables) to a logiset with scalar-valued features. Refer to [`islogiseed`](@ref) for the interface that `dataset` must adhere to.

# Arguments

  * `dataset`: the dataset that will be transformed into a logiset. It should adhere to the [`islogiseed`](@ref) interface;
  * `features`: vector of features, corresponding to `dataset` columns;

# Keyword Arguments

  * `use_onestep_memoization::Union{Bool,Type{<:AbstractOneStepMemoset}}=!isnothing(conditions) && !isnothing(relations)`:

enable one-step memoization, optimizing the checking of specific, short formulas using specific scalar conditions and relations (see [`AbstractOneStepMemoset`](@ref));

  * `conditions::Union{Nothing,AbstractVector{<:AbstractCondition}}=nothing`:

a set of conditions or metaconditions to be used in one-step memoization. If not provided, metaconditions given by minimum and maximum applied to each variable will be used (see [`ScalarMetaCondition`](@ref));

  * `relations::Union{Nothing,AbstractVector{<:AbstractRelation}}=nothing`:

a set of relations to be used in one-step memoization (see [`AbstractRelation`](@ref));

  * `onestep_precompute_globmemoset::Bool = (use_onestep_memoization != false)`:

precompute the memoization set for global one-step formulas. This usually takes little time: in facto, because, global formulas are grounded, the intermediate `check` result does not depend on the number of worlds.

  * `onestep_precompute_relmemoset::Bool = false`:

precompute the memoization set for global one-step formulas. This may take a long time, depending on the relations and the number of worlds; it is usually not needed.

  * `use_full_memoization::Union{Bool,Type{<:Union{AbstractOneStepMemoset,AbstractFullMemoset}}}=true`:

enable full memoization, where every intermediate `check` result is cached to avoid recomputing. This can be used in conjunction with one-step memoization;

  * `print_progress::Bool = false`: print a progress bar;
  * `allow_propositional::Bool = false`: allows a tabular (i.e, non-relational) dataset to be instantiated as a `PropositionalLogiset`, instead of a modal logiset;
  * `force_i_variables::Bool = false`: when conditions are to be inferred (`conditions = nothing`), force (meta)conditions to refer to variables by their integer index, instead of their `Symbol` name (when available through `varnames`, see [`islogiseed`](@ref)).

# Logiseed-specific Keyword Arguments

  * `worldtype_by_dim::AbstractDict{Int,Type{<:AbstractWorld}}([0 => OneWorld, 1 => Interval, 2 => Interval2D])`:

When the dataset is a [`MultiData.AbstractDimensionalDataset`](@ref), this map between the [`dimensionality`](@ref) and the desired [`AbstractWorld`](@ref) type is used to infer the frame type. By default, dimensional datasets of dimensionalities 0, 1 and 2 will generate logisets based on OneWorld, Interval's, and Interval2D's, respectively.

# Examples

```julia>repl
julia> df = DataFrame(A = [36, 37, 38], B = [1, 2, 3])
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │    36      1
   2 │    37      2
   3 │    38      3

julia> scalarlogiset(df; worldtype_by_dim=([0=>OneWorld]))
SupportedLogiset with 1 support (2.21 KBs)
├ worldtype:                   OneWorld
├ featvaltype:                 Int64
├ featuretype:                 VariableValue
├ frametype:                   SoleLogics.FullDimensionalFrame{0, OneWorld}
├ # instances:                 3
├ usesfullmemo:                true
├[BASE] UniformFullDimensionalLogiset of dimensionality 0 (688.0 Bytes)
│ ├ size × eltype:              (3, 2) × Int64
│ └ features:                   2 -> VariableValue[V1, V2]
└[SUPPORT 1] FullMemoset (0 memoized values, 1.5 KBs))
```

julia> pointlogiset = scalarlogiset(     X*df;     worldtype*by_dim=Dict([1 => SoleLogics.Point1D, 2 => SoleLogics.Point2D]) )

See also [`AbstractModalLogiset`](@ref), [`AbstractOneStepMemoset`](@ref), `SoleLogics.AbstractRelation`, `SoleLogics.AbstractWorld`, [`ScalarCondition`](@ref), [`VarFeature`](@ref).
