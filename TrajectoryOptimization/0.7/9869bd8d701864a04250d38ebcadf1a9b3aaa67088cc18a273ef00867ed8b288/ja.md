```
DiagonalCost{n,m,T}
```

コスト関数の形

$$
\frac{1}{2} x^T Q x + \frac{1}{2} u^T R u + q^T x + r^T u + c
$$

ここで、$Q$ と $R$ はそれぞれ正半定値および正定値の対角行列であり、$x$ は `n` 次元、$u$ は `m` 次元です。

# コンストラクタ

```
DiagonalCost(Qd, Rd, q, r, c; kwargs...)
DiagonalCost(Q, R, q, r, c; kwargs...)
DiagonalCost(Qd, Rd; [q, r, c, kwargs...])
DiagonalCost(Q, R; [q, r, c, kwargs...])
```

ここで、`Qd` と `Rd` は対角ベクトルであり、`Q` と `R` は行列です。

任意のオプションまたは省略された値はゼロに設定されます。キーワード引数は次のとおりです。

  * `terminal` - コスト関数が終端コストであるかどうかを指定する `Bool`。
  * `checks` - `Q` と `R` が必要な定値性をチェックされるかどうかを指定する `Bool`。
