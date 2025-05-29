# Outer constructors

  * [`Strand(strand::Char)`](@ref)
  * [`Strand(strand::UInt8)`](@ref)

[`Strand`](@ref) can take four kinds of values listed in the next table:

| Symbol | Constant              | Meaning                           |
|:------ |:--------------------- |:--------------------------------- |
| `'?'`  | [`STRAND_NA`](@ref)   | strand is unknown or inapplicable |
| `'+'`  | [`STRAND_POS`](@ref)  | positive strand                   |
| `'-'`  | [`STRAND_NEG`](@ref)  | negative strand                   |
| `'.'`  | [`STRAND_BOTH`](@ref) | non-strand-specific feature       |
