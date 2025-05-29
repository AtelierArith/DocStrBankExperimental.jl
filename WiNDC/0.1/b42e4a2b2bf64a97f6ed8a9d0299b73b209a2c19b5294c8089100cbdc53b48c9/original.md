```
subset(
        data::T, 
        @nospecialize(args...)
    ) where T <: WiNDCtable
```

Return a subset of `data` based on the conditions given in `args`. This will  subset both the main table and the set table.

## Required Arguments

  * `data::T`: The `WiNDCtable` to subset.
  * `args::Tuple`: Pairs of the form `set_name => boolean function`.

## Return

A table of type `T`.
