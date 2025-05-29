```
Cols(cols...; operator=union)
Cols(f::Function; operator=union)
```

Select columns matching specifications in `cols`. If `cols == ()`, select no columns.

If the only positional argument is a `Function` `f` then select the columns whose names passed to the `f` predicate as strings return `true`.

When multiple `cols` selectors are passed then the sets of columns selected by them are passed to `operator` as positional arguments. `operator` should be a set operation function, like `union`, `intersect`, `setdiff`, and `symdiff` defined in Base Julia. By default `operator=union` in which case all columns matching at least one selector are returned.
