```
PauliFreqTracker(coeff::Number, nsins::Int, ncos::Int, freq::Int)
```

`PauliRotation`ゲートを介して適用されるsinおよびcos因子の数と、それらの合計であるいわゆる周波数を記録する、パウリ伝播における数値係数のラッパー型です。これらの3つのプロパティは、マージがそれらにどのように影響するかのために別々に追跡する必要があるため、冗長に見えるかもしれません。
