```
prefilter(d::AbstractIdData, l::Number, u::Number)
```

入力と出力を `l` と `u` Hz の間のバンドパスフィルターでフィルタリングします。`l = 0` の場合はローパスフィルターが使用され、`u = Inf` の場合はハイパスフィルターが使用されます。
