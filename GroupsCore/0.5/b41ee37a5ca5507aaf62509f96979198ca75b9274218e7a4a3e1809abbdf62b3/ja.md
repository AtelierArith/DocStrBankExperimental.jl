```
istrivial(M::Monoid)
```

モノイド `M` が自明であるかどうかをテストします。

デフォルトの実装は `isfinite` と `order` に基づいています。
