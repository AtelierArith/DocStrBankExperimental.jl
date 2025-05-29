```
unsafe_comparisons(onoff=true; verbose=true)
```

Toggle the use of a comparison function without warning. By default `mean` is used to reduce particles to a floating point number for comparisons. This function can be changed, example: `set_comparison_function(median)`

```
unsafe_comparisons(mode=:reduction; verbose=true)
```

One can also specify a comparison mode, `mode` can take the values `:safe, :montecarlo, :reduction`. `:safe` is the same as calling `unsafe_comparisons(false)` and `:reduction` corresponds to `true`. If
