```
rename!(df::AbstractDataFrame, vals::AbstractVector{Symbol};
        makeunique::Bool=false)
rename!(df::AbstractDataFrame, vals::AbstractVector{<:AbstractString};
        makeunique::Bool=false)
rename!(df::AbstractDataFrame, (from => to)::Pair...)
rename!(df::AbstractDataFrame, d::AbstractDict)
rename!(df::AbstractDataFrame, d::AbstractVector{<:Pair})
rename!(f::Function, df::AbstractDataFrame; cols=All())
```

Rename columns of `df` in-place. Each name is changed at most once. Permutation of names is allowed.

# Arguments

  * `df` : the `AbstractDataFrame`
  * `d` : an `AbstractDict` or an `AbstractVector` of `Pair`s that maps the original names or column numbers to new names
  * `f` : a function which for each column selected by the `cols` keyword argument takes the old name as a `String` and returns the new name that gets converted to a `Symbol`; the `cols` column selector can be any value accepted as column selector by the `names` function
  * `vals` : new column names as a vector of `Symbol`s or `AbstractString`s of the same length as the number of columns in `df`
  * `makeunique` : if `false` (the default), an error will be raised if duplicate names are found; if `true`, duplicate names will be suffixed with `_i` (`i` starting at 1 for the first duplicate).

If pairs are passed to `rename!` (as positional arguments or in a dictionary or a vector) then:

  * `from` value can be a `Symbol`, an `AbstractString` or an `Integer`;
  * `to` value can be a `Symbol` or an `AbstractString`.

Mixing symbols and strings in `to` and `from` is not allowed.

Metadata: this function preserves table-level and column-level `:note`-style metadata.

Metadata having other styles is dropped (from parent data frame when `df` is a `SubDataFrame`). Column-level `:note`-style metadata is considered to be attached to column number: when a column is renamed, its `:note`-style metadata becomes associated to its new name.

See also: [`rename`](@ref)

# Examples

```jldoctest
julia> df = DataFrame(i=1, x=2, y=3)
1×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(df, Dict(:i => "A", :x => "X"))
1×3 DataFrame
 Row │ A      X      y
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(df, [:a, :b, :c])
1×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(df, [:a, :b, :a])
ERROR: ArgumentError: Duplicate variable names: :a. Pass makeunique=true to make them unique using a suffix automatically.

julia> rename!(df, [:a, :b, :a], makeunique=true)
1×3 DataFrame
 Row │ a      b      a_1
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(uppercase, df)
1×3 DataFrame
 Row │ A      B      A_1
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> rename!(lowercase, df, cols=contains('A'))
1×3 DataFrame
 Row │ a      B      a_1
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

```
