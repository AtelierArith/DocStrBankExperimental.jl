```
fpswhen(switch, rate)
```

は、`switch` 信号が真のときに、毎秒 `rate` 回更新される信号を返します。もし、依存する信号値の計算が遅いために `rate` を達成できない場合、信号は可能な限り最良のレートを提供するように自己調整します。
