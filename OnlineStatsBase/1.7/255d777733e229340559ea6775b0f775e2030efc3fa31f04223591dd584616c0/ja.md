```
merge!(a, b)
```

`OnlineStat` `b`を`a`にマージします（ほとんどの`OnlineStat`タイプでサポートされています）。

# 例

```
a = fit!(Mean(), 1:10)
b = fit!(Mean(), 11:20)
merge!(a, b)
```
