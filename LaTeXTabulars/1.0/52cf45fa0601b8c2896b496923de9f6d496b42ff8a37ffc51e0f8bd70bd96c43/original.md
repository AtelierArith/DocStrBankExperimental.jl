```julia
latex_tabular(io, t, lines; formatter)

```

Print `lines` to `io` as a LaTeX using the given environment.

Each `line` in `lines` can be

  * a rule-like object, eg [`Rule`](@ref) or [`CMidRule`](@ref),
  * an iterable (eg `AbstractVector`) of cells,
  * a `Tuple`, which is treated as multiple lines (“splat” in place), which is useful for functions that generate lines with associated rules, or multiple `CMidRule`s,
  * a matrix, each row of which is treated as a line.

Constructs which contain cells are printed by [`latex_cell`](@ref), using the `formatter`, which leaves strings and `LaTeX` cells as is.

It is recommended that formatting parts of the table is done directly on the arguments, using a suitable formatter. See the manual for examples.

See [`latex_cell`](@ref) for the kinds of cell supported (particularly [`MultiColumn`](@ref), but for full formatting control, use an `String` or `LaTeXString` for cells.
