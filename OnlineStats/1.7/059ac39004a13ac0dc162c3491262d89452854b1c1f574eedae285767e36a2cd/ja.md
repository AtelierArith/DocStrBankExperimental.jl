```
StatLag(stat, b)
```

`stat`の移動ウィンドウ（前の`b`コピー）を追跡します。

# 例

```
fit!(StatLag(Mean(), 10), 1:20)
```
