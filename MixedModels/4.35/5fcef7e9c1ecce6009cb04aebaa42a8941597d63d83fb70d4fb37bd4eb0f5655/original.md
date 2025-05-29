```
BlockDescription
```

Description of blocks of `A` and `L` in a [`LinearMixedModel`](@ref)

## Fields

  * `blknms`: Vector{String} of block names
  * `blkrows`: Vector{Int} of the number of rows in each block
  * `ALtypes`: Matrix{String} of datatypes for blocks in `A` and `L`.

When a block in `L` is the same type as the corresponding block in `A`, it is described with a single name, such as `Dense`.  When the types differ the entry in `ALtypes` is of the form `Diag/Dense`, as determined by a `shorttype` method.
