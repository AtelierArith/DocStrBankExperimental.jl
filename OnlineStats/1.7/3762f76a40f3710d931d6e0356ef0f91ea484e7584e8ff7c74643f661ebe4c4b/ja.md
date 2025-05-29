```
Diff(T::Type = Float64)
```

差分と最後の値を追跡します。

# 例

```
o = Diff()
fit!(o, [1.0, 2.0])
last(o)
diff(o)
```
