```
elementwise(f)
```

`Base.Fix1(broadcast, f)`のエイリアスです。

`f::ComposedFunction`の場合、結果は`Base.Fix1(broadcast, f.outer) ∘ Base.Fix1(broadcast, f.inner)`となり、`Base.Fix1(broadcast, f)`にはなりません。
