```
read_from_file(
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

Return a JuMP model read from `filename` in the format `format`.

See [`MOI.FileFormats.FileFormat`](@ref) for a list of supported formats.

## Keyword arguments

Other `kwargs` are passed to the `Model` constructor of the chosen format.

For details, see the docstring each file format's `Model` constructor. For example, [`MOI.FileFormats.MPS.Model`](@ref).

## Nonlinear models

To maintain backwards compatibility, nonlinear models in `.mof.json` and `.nl` files are parsed into a [`MOI.NLPBlock`](@ref). To parse as [`MOI.ScalarNonlinearFunction`](@ref), pass the keyword `use_nlp_block = false`.

## Compression

If the filename ends in `.gz`, the file will be uncompressed using GZip.

If the filename ends in `.bz2`, the file will be uncompressed using BZip2.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> @objective(model, Min, log(x));

julia> filename = joinpath(mktempdir(), "model.mof.json");

julia> write_to_file(model, filename)

julia> new_model = read_from_file(filename; use_nlp_block = false)
A JuMP Model
├ solver: none
├ objective_sense: MIN_SENSE
│ └ objective_function_type: NonlinearExpr
├ num_variables: 1
├ num_constraints: 1
│ └ VariableRef in MOI.GreaterThan{Float64}: 1
└ Names registered in the model: none

julia> print(new_model)
Min log(x)
Subject to
 x ≥ 0
```
