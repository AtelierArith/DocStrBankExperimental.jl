```
pulse(delta::TimePeriod[; epoch::DateTime])
```

`delta` ごとにティックするノードを取得します。各値はノットの時間と等しくなります。

ノットは、その時間と `epoch` との間の差が常に `delta` の整数倍になるように配置されます。デフォルトでは、`epoch` は Julia の `DateTime` エポックに設定されており、それは `DateTime(0, 12, 31)` です。
