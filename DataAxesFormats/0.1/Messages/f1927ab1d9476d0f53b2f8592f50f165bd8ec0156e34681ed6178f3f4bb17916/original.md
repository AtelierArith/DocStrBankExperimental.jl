```
unique_name(prefix::AbstractString, separator::AbstractString = "#")::AbstractString
```

Using short, human-readable unique names for things is a great help when debugging. Normally one has to choose between using a human-provided short non-unique name, and an opaque object identifier, or a combination thereof. This function replaces the opaque object identifier with a short counter, which gives names that are both unique and short.

That is, this will return a unique name starting with the `prefix` and followed by the `separator` (by default, `#`), the process index (if using multiple processes), and an index (how many times this name was used in the process). For example, `unique_name("foo")` will return `foo` for the first usage, `foo#2` for the 2nd, etc. If using multiple processes, it will return `foo`, `foo#1.2`, etc.

That is, for code where the names are unique (e.g., a simple script or Jupyter notebook), this doesn't mess up the names. It only appends a suffix to the names if it is needed to disambiguate between multiple uses of the same name.

To help with tests, if the `prefix` contains `!`, we return it as-is, accepting it may not be unique.
