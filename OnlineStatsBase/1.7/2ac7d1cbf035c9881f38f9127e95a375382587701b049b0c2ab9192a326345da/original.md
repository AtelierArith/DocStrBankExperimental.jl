```
SkipMissing(stat)
```

Wrapper around an OnlineStat that will skip over `missing` values.

# Example

```
o = SkipMissing(Mean())

fit!(o, [1, missing, 3])
```
