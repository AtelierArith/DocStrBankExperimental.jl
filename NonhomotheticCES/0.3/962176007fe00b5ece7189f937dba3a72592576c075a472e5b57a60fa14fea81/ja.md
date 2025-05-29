```julia
NonhomotheticCESUtility(σ, Ω̂s, ϵs)

```

非同次CES選好、定義如下

*Comin, D., Lashkari, D., & Mestieri, Martí (2021). Structural change with long-run  income and price effects. Econometrica, 89(1), 311–374.*

### 定義

$$
E = ∑ᵢ pᵢ Cᵢ
$$

は *総支出* を示します。消費集約関数 `C` は以下のように暗黙的に定義されます。

$$
E^{1 - \sigma} = \sum_i \Omega_i (C^{\epsilon_i} p_i)^{1 - \sigma}
$$

実際の計算とパラメータ化では、浮動小数点精度を向上させるために対数（$Ê = log(E)$ など）を使用します。

### 引数

  * `σ`: 異なるセクター間の代替弾力性、`> 0`、`≠ 1`。
  * `Ω̂s`: **対数**のセクター重み
  * `ϵs`: セクターの非同次性パラメータ。

### 提案

  * 可能な限りベクトル引数には `SVector` を使用してください。
  * いくつかの方法で正規化することを検討してください。例えば、論文の式（10）で説明されているように、*基準財* のために `ϵ = 1` および `Ω̂ = 0` に正規化することです。
