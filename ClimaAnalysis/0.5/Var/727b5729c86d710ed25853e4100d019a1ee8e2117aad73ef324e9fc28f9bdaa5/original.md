```
replace(var::OutputVar, old_new::Pair...)
```

Return a `OutputVar` where, for each pair `old  => new`, all occurences of `old` are replaced by `new` in `Var.data`

This function is useful if there are `NaN`s or `missing` values in the data. For instance, you want to use the ocean mask, but there are `NaN`s in the ocean. You can replace all the `NaN` and `missing` values with 0.0 and apply the ocean mask afterward.
