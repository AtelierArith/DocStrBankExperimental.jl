```
CountMissing(stat)
```

Calculate a `stat` along with the count of `missing` values.  

# Example

```
o = CountMissing(Mean())
fit!(o, [1, missing, 3])
```
