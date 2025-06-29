```
Secant()
Order1()
Orderφ()
```

`Order1()` メソッドは `Secant` のエイリアスです。これは [セカント法](https://en.wikipedia.org/wiki/Secant_method) を指定します。このメソッドは、状態に `xₙ` と `xₙ₋₁` の2つの値を保持します。更新された点は、2つの点から形成されたセカント線と $x$ 軸の交点です。セカント法は、ステップごとに $1$ 回の関数評価を使用し、次数は `φ≈ (1+sqrt(5))/2` です。

誤差 `eᵢ = xᵢ - α` は、`eᵢ₊₂ = f[xᵢ₊₁,xᵢ,α] / f[xᵢ₊₁,xᵢ] * (xᵢ₊₁-α) * (xᵢ - α)` を満たします。
