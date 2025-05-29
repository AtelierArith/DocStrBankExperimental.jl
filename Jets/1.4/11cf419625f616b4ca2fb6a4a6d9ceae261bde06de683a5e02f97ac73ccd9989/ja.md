```
jacobian(F, mₒ)
```

`F::Union{Jet, Jop, AbstractMatrix}` の点 `m₀` でのヤコビアンを返します。線形化は新しい基礎となる `Jet` を構築します。
