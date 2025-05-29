```
FilterTransform(stat::OnlineStat{S}, T = S; filter = x->true, transform = identity)
FilterTransform(T => filter => transform => stat)
```

Wrapper around an OnlineStat that the filters and transforms its input.  Note that, depending on  your transformation, you may need to specify the type of a single observation (`T`).

# Examples

```
o = FilterTransform(Mean(), Union{Missing,Number}, filter=!ismissing)
fit!(o, [1, missing, 3])

o = FilterTransform(String => (x->true) => (x->parse(Int,x)) => Mean())
fit!(o, "1")
```
