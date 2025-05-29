Holds one puzzle instance.

# Fields of `Puzzle{T}`

  * `palette`: Iterable collection of the puzzle's permitted colors, each of type `T`. Lack of color is represented by `zero(T)`, so `zero(T)` must be defined and must not be in `palette`.
  * `sR::Vector{Vector{Int}}`: Numerical clues for each row, from top to bottom. Empty rows are entered as `Int[]` (and *not* e.g. `[0]`).
  * `cR::Vector{Vector{T}}`: Colors in `palette` corresponding to the clues in `sR`.
  * `sC::Vector{Vector{Int}}`: Numerical clues for each column, from left to right. Empty columns are entered as `Int[]`.
  * `cC::Vector{Vector{T}}`: Colors in `palette` corresponding to the clues in `sC`.

# Non-default constructors

The following constructors for `Puzzle` are recommended over the default constructor.

## For monochrome puzzles

```
Puzzle(sR::Vector{Vector{Int}}, sC::Vector{Vector{Int}})
```

Hold a monochrome puzzle, with `sR` containing row clues and `sC` containing column clues.

This constructor sets the puzzle's single color (traditionally "black") to `1`, lack of color (traditionally "white") to `0`, and `Puzzle.palette` to `1:1`.

## For multicolored puzzles

```
Puzzle(sR, cR, sC, cC)
```

Build `Puzzle.palette` from `cR` and `cC`; otherwise identical to the default constructor.

See also [`read_puzzle_from_cwc`](@ref).
