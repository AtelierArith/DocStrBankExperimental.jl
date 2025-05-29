```
Concat(args...)
```

Create a `Concat` object which can be used to concatenate the representations of multiple values in a single table cell while keeping the conversion semantics of each `arg` in `args` intact.

## Example

```julia
Concat(
    "Some text and an ",
    Annotated("annotated", "Some annotation"),
    " value",
)
# will be rendered as "Some text and an annotated¹ value"
```
