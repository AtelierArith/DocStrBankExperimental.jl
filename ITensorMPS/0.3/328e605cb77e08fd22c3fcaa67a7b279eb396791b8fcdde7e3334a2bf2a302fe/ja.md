```
noise!(sw::Sweeps,maxdims::Int...)
```

各スイープに使用されるノイズ項の係数を設定するには、最大 `nsweep(sw)` の値を提供します。提供される値が少ない場合、最後の値が残りのスイープに対して繰り返されます。
