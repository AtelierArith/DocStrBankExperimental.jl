```
Is0to1(X) :: Query
```

This query asserts that `X` emits 0 or 1 element.

---

```
Each(X >> Is0to1) :: Query
```

In this form, `Is0to1` asserts that its input contains 0 or 1 element.
