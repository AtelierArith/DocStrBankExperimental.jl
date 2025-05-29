```
Is0toN(X) :: Query
```

This query asserts that `X` may emit any number of elements.

---

```
Each(X >> Is0toN) :: Query
```

In this form, `Is0toN` asserts that its input contains any number of elements.
