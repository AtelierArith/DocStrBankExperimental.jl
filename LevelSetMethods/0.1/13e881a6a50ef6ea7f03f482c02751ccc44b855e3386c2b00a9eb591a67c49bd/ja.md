```
struct ReinitializationTerm <: LevelSetTerm
```

レベルセット項は `sign(ϕ) (|∇ϕ| - 1)` を表します。この `LevelSetTerm` は、レベルセットを符号付き距離関数に再初期化するために使用されるべきです：十分に多くの時間ステップに対して、この項はエイコナル方程式 |∇ϕ| = 1 を解くことを可能にします。
