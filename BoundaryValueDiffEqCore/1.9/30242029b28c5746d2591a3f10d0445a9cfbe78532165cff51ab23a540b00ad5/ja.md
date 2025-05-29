```
DefectControl(; defect_threshold = 0.1)
```

欠陥推定方法は、欠陥が次のように定義されます

$$
defect = \max\frac{S'(x) - f(x,S(x))}{1 + |f(x,S(x))|}
$$

欠陥コントローラーは、最大 `defect_threshold` が 0.1 であり、推定された欠陥が `defect_threshold` より大きい場合、メッシュが細分化されます。
