```
compute!(df::DataFrame; verbose=true, fail_fast=true)
```

`df`の各行についてテストとベンチマークを実行します。

ベンチマーク結果は`df.data`に保存されます。
