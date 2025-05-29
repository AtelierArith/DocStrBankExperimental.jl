```
abstract type AbstractNonDisRES <: EMB.Source
```

すべての非 dispatchable 再生可能エネルギー源のための抽象スーパタイプ。[`NonDisRES`](@ref) の実装バージョンのすべての関数は、このスーパタイプに対してディスパッチされます。
