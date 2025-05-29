```
toarray(lv::LabeledValues)
```

`toarray(...)` and `fromarray(...)` are a pair of functions for making `LabeledValues` compatible with functions that take as arguments a vector of Float64.  This is common for non-linear optimization functions.  `toarray(lv)` takes a `LabeledValues` and returns an ordered vector of Float64.  `fromarray(f,lv)` is a little more subtle as it returns a function `g` such that `g(toarray(lv)) = f(lv)`.  That is, `fromarray(...)` allows you to use `f(lv)` as an argument to functions that expect a vector argument.
