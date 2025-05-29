```
DefectControl(; defect_threshold = 0.1)
```

Defect estimation method with defect defined as

$$
defect = \max\frac{S'(x) - f(x,S(x))}{1 + |f(x,S(x))|}
$$

Defect controller, with the maximum `defect_threshold` as 0.1, when the estimating defect is greater than the `defect_threshold`, the mesh will be refined.
