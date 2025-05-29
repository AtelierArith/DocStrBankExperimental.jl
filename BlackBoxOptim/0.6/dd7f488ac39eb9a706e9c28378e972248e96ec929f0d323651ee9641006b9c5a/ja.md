```
dimrange(ss::SearchSpace, [i::Integer])
```

`ss`の`i`-次元の最小および最大の有効値の`ParamsRange`タプルを取得します。`i`が指定されていない場合は、各次元の`ParamsRange`タプルのベクトルを取得します。
