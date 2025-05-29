`objgrad!(f, t, g)` は `LineModel` の目的関数と一次導関数を評価します。

```
ϕ(t) := f(x + td),
```

および

```
ϕ'(t) = ∇f(x + td)ᵀd.
```

勾配 ∇f(x + td) は `g` に格納されます。
