```
QuadraticCost{n,m,T,TQ,TR}
```

コスト関数の形

$$
\frac{1}{2} x^T Q x + \frac{1}{2} u^T R u + u^T H x + q^T x + r^T u + c
$$

ここで、$R$ は正定値でなければならず、$Q$ と $Q_f$ は半正定値でなければなりません。

型パラメータ `TQ` と `TR` は $Q$ と $R$ の型を指定します。

# コンストラクタ

```
QuadraticCost(Q, R, H, q, r, c; kwargs...)
QuadraticCost(Q, R; H, q, r, c, kwargs...)
```

任意のオプションまたは省略された値はゼロに設定されます。キーワード引数は次のとおりです。

  * `terminal` - コスト関数が終端コストであるかどうかを指定する `Bool`。
  * `checks` - `Q` と `R` が必要な定値性をチェックされるかどうかを指定する `Bool`。
