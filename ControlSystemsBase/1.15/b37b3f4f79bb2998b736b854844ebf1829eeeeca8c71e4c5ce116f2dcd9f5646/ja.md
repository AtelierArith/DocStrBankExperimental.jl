```
struct DelayLtiSystem{T, S <: Real} <: LTISystem
```

内部時間遅延を持つLTISystemを表します。便利なコンストラクタについては`?delay`を参照してください。
