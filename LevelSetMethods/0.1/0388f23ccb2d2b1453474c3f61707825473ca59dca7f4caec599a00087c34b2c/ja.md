```
struct NormalMotionTerm{V,M} <: LevelSetTerm
```

レベルセットの輸送項を表す `v |∇ϕ|`。この `LevelSetTerm` は内部生成された速度場に使用するべきです; 外部生成された速度には代わりに `AdvectionTerm` を使用することができます。
