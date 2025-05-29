```
perfstat(A)
```

A::Union{Jet,Jop,JopAdjoint}のパフォーマンス情報を持つ`Dictionary`を返します。`perfstat(jet::Jet)`メソッドは、演算子の著者によって実装され、パフォーマンスメトリックを追跡するために使用されます。
