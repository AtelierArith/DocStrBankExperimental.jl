```
Assert(; cond, msg="")
```

Asserts all columns of the table by throwing a `AssertionError(msg)` if `cond(column)` returns `false`, otherwise returns the input table.

The `msg` argument can be a string, or a function that receives the column name and returns a string, e.g.: `nm -> "error in column $nm"`.

```
Assert(col₁, col₂, ..., colₙ; cond, msg="")
Assert([col₁, col₂, ..., colₙ]; cond, msg="")
Assert((col₁, col₂, ..., colₙ); cond, msg="")
```

Asserts the selected columns `col₁`, `col₂`, ..., `colₙ`.

```
Assert(regex; cond, msg="")
```

Asserts the columns that match with `regex`.

# Examples

```julia
Assert(cond=allunique, msg="assertion error")
Assert([2, 3, 5], cond=x -> sum(x) > 100)
Assert([:b, :c, :e], cond=x -> eltype(x) <: Integer)
Assert(("b", "c", "e"), cond=allunique, msg=nm -> "error in column $nm")
Assert(r"[bce]", cond=x -> sum(x) > 100)
```
