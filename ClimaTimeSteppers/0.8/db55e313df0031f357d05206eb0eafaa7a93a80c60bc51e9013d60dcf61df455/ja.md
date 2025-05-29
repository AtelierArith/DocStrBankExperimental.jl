```
MinimumRateOfConvergence(rate, order = 1)
```

`err[iter] ≥ rate * err[iter - 1]^order` がすべての `iter ≥ 1` に対して成り立つかどうかをチェックします。`err[iter] ≥ 0` であるため、これは `rate ≥ 0` の場合にのみ `true` になります。また、`order == 1` の場合、列が発散しないためには `rate ≤ 1` である必要があります（すなわち、`err[iter] > err[iter - 1]` を避けるため）。さらに、すべての十分大きな値の `iter` に対して `err[iter] < 1` である場合、列が発散しないためには `order ≥ 1` である必要があります。
