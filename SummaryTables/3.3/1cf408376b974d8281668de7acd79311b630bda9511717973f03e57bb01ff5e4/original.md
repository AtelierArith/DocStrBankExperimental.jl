```
Multiline(args...)
```

Create a `Multiline` object which renders each `arg` on a separate line. A `Multiline` value may only be used as the top-level value of a cell, so `Cell(Multiline(...))` is allowed but `Cell(Concat(Multiline(...), ...))` is not.
