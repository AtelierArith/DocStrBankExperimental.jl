任意の `k::TransitionKernel` に対して、`basekernel` は次の条件を満たすことが期待されます。

```
basekernel(k)(p) == (basemeasure ∘ k)(p)
```

`basekernel` の主な目的は、次の計算を効率的に行うことです。

```
basemeasure(d::ProductMeasure) == productmeasure(basekernel(d.f), d.xs)
```
