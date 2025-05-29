```
bubblebath(
    radius_pdf, ϕ_max::Real, extent::NTuple{D,Real};
    through_boundaries = false,
    max_tries = 10000, max_fails = 100,
    verbose = true
) where D
```

ドメイン `extent` に球のバスを生成し、`radius_pdf` から半径を抽出して目標充填率 `ϕ_max` に到達しようとします。ドメインは半径が減少する順に球で満たされます。

## キーワード

  * `min_distance = 0.0`: 球の間に許可される最小距離。重なりを許可するために負の値を使用できます。
  * `through_boundaries = false`: 球がドメインの境界を越えて移動できるかどうか。
  * `max_tries = 10000`: 各球の挿入試行の最大回数。 `max_tries` に達した場合、球は破棄され、アルゴリズムは次の球に進みます。
  * `max_fails = 100`: 許可される失敗（すなわち破棄された球）の最大数。 `max_fails` に達した場合、プログラムは停止します。
  * `verbose = true`: 情報ログを印刷するかどうか。
  * `rng = Random.default_rng()`: 擬似乱数生成器。

負の `min_distance` が使用されるか、`through_boundaries` が true に設定されている場合、生成中に推定される充填率はシステムの実際の充填率に対応しません。このような場合、`ϕ_max` は *半* 定量的な値のみを持ちます。
