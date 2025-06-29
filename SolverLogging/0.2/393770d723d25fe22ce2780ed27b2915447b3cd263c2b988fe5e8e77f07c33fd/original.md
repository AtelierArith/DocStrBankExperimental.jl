```
ConditionalCrayon
```

Sets conditional formatting for printing to the terminal. Each `ConditionalCrayon`  specifies a function `bad(x)` that returns `true` if the argument `x` is not acceptable, printing with color `cbad`, and a function `good(x)` that returns `true` if `x` is  acceptable, printing with color `cgood`. If neither are true then `cdefault` is the  color. The `bad` function will be checked before `good`, so takes precedence if both  happen to return `true`. This is not checked.

All colors must be specified as a Crayon type from Crayons.jl

# Constructors

Usage will generally be through the following constructor:

```
ConditionalCrayon(badfun::Function, goodfun::Function; [goodcolor, badcolor, defaultcolor])
```

The colors default to green for good, red for bad, and default color (`Crayon(reset=true)`)  for the default.

For convenience when working with ranges, the following constructor is also provided:

```
ConditionalCrayon(lo, hi; [reverse, goodcolor, badcolor, defaultcolor])
```

Which will be good if the value is less than `lo` and bad if it's higher than `hi`. This is reversed if `reverse=true`.

A default constructor

```
ConditionalCrayon()
```

Is also provided, which always returns the default color.

# Usage

The `ConditionalCrayon` is a functor object that accepts a single argument of any type, and returns the `Crayon` according to the output of the `good` and `bad` functions on that input. It's the user's responsibility to make sure the input type is appropriate for the  functions (since these are all user-specified).
