```
gather_array(val::Symbol, workers, dim=1; free=false)
```

Collect the arrays distributed on `workers` under value `val` into an array. The individual arrays are pasted in the dimension specified by `dim`, i.e. `dim=1` is roughly equivalent to using `vcat`, and `dim=2` to `hcat`.

`val` must be an Array-based type; the function will otherwise fail.

If `free` is true, the `val` is `unscatter`ed after being gathered.

This preallocates the array for results, and is thus more efficient than e.g. using `dmapreduce` with `vcat` for folding.
