# Extended help

```
complement(X::LazySet)
```

### Algorithm

The default implementation assumes that `X` is polyhedral and returns a `UnionSetArray` of `HalfSpace`s, i.e., the output is the union of the linear constraints which are obtained by complementing each constraint of `X`. For any pair of sets $(X, Y)$ we have the identity $(X ∩ Y)^C = X^C ∪ Y^C$. We can apply this identity for each constraint that defines a polyhedral set.
