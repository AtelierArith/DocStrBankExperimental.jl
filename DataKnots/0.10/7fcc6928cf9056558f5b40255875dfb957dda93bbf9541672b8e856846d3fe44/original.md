```
Is1toN(X) :: Query
```

This query asserts that `X` emits 1 or more elements.

---

```
Each(X >> Is1toN) :: Query
```

In this form, `Is1toN` asserts that its input contains 1 or more elements.
