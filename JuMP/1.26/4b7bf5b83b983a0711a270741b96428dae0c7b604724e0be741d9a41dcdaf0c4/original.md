```
write_to_file(
    model::GenericModel,
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

Write the JuMP model `model` to `filename` in the format `format`.

See [`MOI.FileFormats.FileFormat`](@ref) for a list of supported formats.

## Compression

If the filename ends in `.gz`, the file will be compressed using GZip.

If the filename ends in `.bz2`, the file will be compressed using BZip2.

## Keyword arguments

Other `kwargs` are passed to the `Model` constructor of the chosen format.

For details, see the docstring each file format's `Model` constructor. For example, [`MOI.FileFormats.MPS.Model`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> @objective(model, Min, 2 * x + 1);

julia> filename = joinpath(mktempdir(), "model.mps");

julia> write_to_file(model, filename; generic_names = true)

julia> print(read(filename, String))
NAME
ROWS
 N  OBJ
COLUMNS
    C1        OBJ       2
RHS
    rhs       OBJ       -1
RANGES
BOUNDS
 LO bounds    C1        0
 PL bounds    C1
ENDATA
```

## Solver-specific formats

[`write_to_file`](@ref) calls a Julia function from the MathOptInterface package that is independent of the choice of solver. That is, it does not call a solver's internal API to write a model to disk.

For MPS files in particular, [`write_to_file`](@ref) may not support the full range of features that a solver's internal API supports. This is because some solvers have defined solver-specific extensions to the MPS format, whereas our Julia implementation supports only features which are standardized across multiple solvers.

To write a file to disk using the solver's internal API, use [`direct_model`](@ref) and call the solver's C API. For example:

```jldoctest
julia> import HiGHS

julia> model = direct_model(HiGHS.Optimizer());

julia> set_silent(model)

julia> @variable(model, x >= 0);

julia> @objective(model, Min, 2 * x + 1);

julia> filename = joinpath(mktempdir(), "model.mps");

julia> HiGHS.Highs_writeModel(backend(model), filename);

julia> print(read(filename, String))
NAME
ROWS
 N  Obj
COLUMNS
    x         Obj       2
RHS
    RHS_V     Obj       -1
ENDATA
```
