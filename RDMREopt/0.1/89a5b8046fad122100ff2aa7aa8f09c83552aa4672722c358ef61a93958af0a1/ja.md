```
Uncertainty(name::String, distribution::Distribution{Univariate, Continuous})
```

入力の不確実性を定義するためのキーワード構造体。

  * `name` 引数は任意の REeopt 入力を指定できます。
  * `distribution` 引数は Distributions.jl の `Distribution{Univariate, Continuous}` 型のいずれかを指定できます。

### 例

```@example
u1 = Uncertainty(
    name="Financial.elec_cost_escalation_pct",
    distribution=Uniform(-0.01, 0.03)    
)
```

### 分布の種類

可能なすべての分布を表示するには、次のコマンドを使用します。

```@example
subtypes(Distribution{Univariate, Continuous})
```

### カスタムサンプルセット

特別なケースとして `ElectricLoad.loads_kw` では、負荷プロファイルのサンプルセットを提供することができます。サンプルセットは均等にサンプリングされます。この機能を使用するには、次のように `Uncertainty` を定義します。

```julia
u4 = Uncertainty(
    "ElectricLoad.loads_kw",
    [
        ones(8760) .* 8.0,  # これらのベクトルをあなたの負荷プロファイルサンプルに置き換えてください
        ones(8760) .* 9.0,
        ones(8760) .* 10.0,
    ]
)
```
