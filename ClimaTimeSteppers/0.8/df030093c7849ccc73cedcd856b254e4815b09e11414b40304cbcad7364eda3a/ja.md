```
MaximumErrorReduction(max_reduction)
```

`err[iter] ≤ max_reduction * err[0]` がすべての `iter ≥ 1` に対して成り立つかどうかをチェックします。`err[iter] ≥ 0` であるため、これは `max_reduction ≥ 0` の場合にのみ `true` になります。また、列が発散しないようにするためには `max_reduction ≤ 1` である必要があります（すなわち、`err[iter] > err[0]` を避けるため）。
