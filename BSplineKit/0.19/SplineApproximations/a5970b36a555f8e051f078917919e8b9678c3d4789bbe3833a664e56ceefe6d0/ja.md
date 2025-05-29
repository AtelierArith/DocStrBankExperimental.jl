```
ApproxByInterpolation <: AbstractApproxMethod
```

与えられた点のセットを通過するスプラインによる近似関数。

点の数は、近似空間を定義するBスプライン基底の長さと等しくなければなりません。

補間点を指定するさまざまな方法については、以下を参照してください。

---

```
ApproxByInterpolation(xs::AbstractVector)
```

与えられた点 `xs` での補間による近似を指定します。

---

```
ApproxByInterpolation(B::AbstractBSplineBasis)
```

与えられた基底に対して適切であると期待される自動的に決定された点のセットでの補間による近似を指定します。

補間点は [`collocation_points`](@ref) を呼び出すことによって決定されます。
