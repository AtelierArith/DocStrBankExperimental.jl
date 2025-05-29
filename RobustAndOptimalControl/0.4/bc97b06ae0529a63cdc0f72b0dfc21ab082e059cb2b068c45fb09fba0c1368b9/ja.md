```
frequency_separation(sys, ω)
```

`sys`を`sys = sys_slow + sys_fast`に分解します。ここで、`sys_slow`は絶対値が`ω`未満の固有値を持つすべてのモードを含み、`sys_fast`は絶対値が`ω`以上の固有値を持つすべてのモードを含みます。
