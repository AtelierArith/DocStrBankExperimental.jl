```
split_interval(I, J, +/-, k) -> Ia, Ib, Ic
```

given unit ranges `I` and `J` and offset `±k`, yields 3 unit ranges, such that `Ia ∪ Ib ∪ Ic = I` and:

  * `∀ i ∈ Ia`, `i ± k < first(J)`;
  * `∀ i ∈ Ib`, `i ± k ∈ J`;
  * `∀ i ∈ Ic`, `i ± k > last(J)`.

Unit ranges may be replaced by their first and last values:

```
split_interval(first(I), last(I), first(J), last(J), +/-, k)
```

yields the same result as above.
