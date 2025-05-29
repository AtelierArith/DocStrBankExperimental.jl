For any `k::TransitionKernel`, `basekernel` is expected to satisfy

```
basekernel(k)(p) == (basemeasure ∘ k)(p)
```

The main purpose of `basekernel` is to make it efficient to compute

```
basemeasure(d::ProductMeasure) == productmeasure(basekernel(d.f), d.xs)
```
