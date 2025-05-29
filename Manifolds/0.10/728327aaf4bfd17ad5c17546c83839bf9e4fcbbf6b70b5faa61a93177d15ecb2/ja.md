```
apply(A::AbstractGroupAction, a, p)
```

アクション `a` を点 `p` に適用し、`A` によって指定されたマップ $τ_a$ を使用します。特に指定がない限り、右作用は左作用に基づいて定義されます：

$$
\mathrm{R}_a = \mathrm{L}_{a^{-1}}
$$
