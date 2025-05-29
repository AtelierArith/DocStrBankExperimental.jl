```
assemble!(model, P, q, constraint(s); [settings, x0, y0, s0])
```

`P`と`q`によって定義されたコスト関数と、いくつかの`constraints`を持つ`COSMO.Model`を組み立てます。

正定値半行列`P`とベクトル`q`は、最適化問題のコスト関数を指定するために使用されます：

```
min   1/2 x'Px + q'x
s.t.  Ax + b ∈ C
```

`constraints`は、`x`に対する制約を記述するために使用される`COSMO.Constraint`または`COSMO.Constraint`オブジェクトの配列です。

---

オプションのキーワード引数`settings`は、カスタムソルバー設定を渡すために使用できます：

```julia
custom_settings = COSMO.Settings(verbose = true);
assemble!(model, P, q, constraints, settings = custom_settings)
```

---

オプションのキーワード引数`x0`と`y0`は、プライマル変数`x`とデュアル変数`y`のウォームスタート値をソルバーに提供するために使用できます。

```julia
x_0 = [1.0; 5.0; 3.0]
COSMO.assemble!(model, P, q, constraints, x0 = x_0)
```
