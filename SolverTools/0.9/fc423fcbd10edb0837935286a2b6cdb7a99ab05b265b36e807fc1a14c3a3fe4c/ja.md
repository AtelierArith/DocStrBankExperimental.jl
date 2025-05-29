`objgrad(f, t)` は `LineModel` の目的関数と一次導関数を評価します。

```
ϕ(t) := f(x + td),
```

および

```
ϕ'(t) = ∇f(x + td)ᵀd.
```
