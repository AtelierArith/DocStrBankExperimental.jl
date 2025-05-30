```
SurrogatesSignificance <: Significance
SurrogatesSignificance(; kwargs...)
```

時系列サロゲートを使用した有意性テスト [`significant_transitions`](@ref) のための構成構造体です。

## キーワード引数

  * `surromethod = RandomFourier()`: サロゲートを生成する方法
  * `n = 1000`: 生成するサロゲートの数
  * `rng = Random.default_rng()`: サロゲート用の乱数生成器
  * `p = 0.05`: p値の有意性の閾値
  * `tail = :both`: 使用されるテールタイプ、以下を参照

## 説明

[`ChangesResults`](@ref) と一緒に使用されると、有意性は次のように推定されます: 入力時系列から `n` サロゲートが `surromethod` を使用して生成されます。これは、[TimeseriesSurrogates.jl](https://juliadynamics.github.io/TimeseriesSurrogates.jl/dev/api/) によって提供される任意の `Surrogate` サブタイプです。各サロゲートについて、指標とその後の変化メトリック時系列が抽出されます。サロゲート変化メトリックの値は、値の分布を形成します（各時点で1つ）。元の変化メトリックの値は、サロゲート分布のそれと比較され、指定された `tail` に従って p値が抽出されます。p値は `p` と比較され、有意性が主張されます。`SurrogatesSignificance` を使用した後、フィールド `.pvalues` でしきい値を設定する前の完全な p値にアクセスできます（例えば、異なる `p` でしきい値を設定するために）。

p値は、各時点で元の変化メトリックを超える（`tail = :right` の場合）または下回る（`tail = :left` の場合）サロゲート変化メトリック値の割合です。サロゲートデータがより高い変化メトリック値を持つと予想される場合は、`tail = :left` を使用します。これはエントロピーを定量化する統計に該当します。自己相関を定量化する統計の場合は、代わりに `tail = :right` を使用します。それ以外の場合は、デフォルトの `tail = :both` を使用します。`tail` 値の反復可能なリストも指定でき、その場合は [`ChangesResults`](@ref) の各変化メトリックに特定の `tail` が使用されます。

生の p値は、`SurrogatesSignificance` を使用して [`significant_transitions`](@ref) 関数を呼び出した後、フィールド `.pvalues` でアクセスできるため、p値の異なるしきい値を取得したい場合に便利です。
