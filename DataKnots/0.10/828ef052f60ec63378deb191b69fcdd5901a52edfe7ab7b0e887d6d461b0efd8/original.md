```
Is1to1(X) :: Query
```

This query asserts that `X` emits 1 element.

---

```
Each(X >> Is1to1) :: Query
```

In this form, `Is1to1` asserts that its input contains 1 element.
