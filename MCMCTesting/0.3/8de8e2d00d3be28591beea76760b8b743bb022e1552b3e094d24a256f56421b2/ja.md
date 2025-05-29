```
mcmctest([rng,] test, subject; kwargs...)
```

`subject` に対して `test` に従って p 値をサンプリングします。

# 引数

  * `rng::Random.AbstractRNG`: 擬似乱数生成器。 (デフォルト: `Random.default_rng()`.)
  * `test::AbstractMCMCTest`: テスト戦略。
  * `subject::TestSubject`: テスト対象の MCMC アルゴリズムとモデル。

# キーワード引数

  * `show_progress::Bool`: 進捗バーを表示するかどうか。 (デフォルト: `true`.)
  * `statistics`: テストから生成されたサンプルからテスト統計を計算するための関数。 (追加の説明については以下のセクションを参照してください。)
  * 追加のキーワード引数については、それぞれのテスト戦略のドキュメントを確認してください。

# カスタムテスト統計

仮説検定に使用される統計は、`statistics` にカスタム関数を渡すことで変更できます。デフォルトの統計は、以下のように計算された第一および第二のモーメントです。

```julia
statistics = params -> vcat(params, params.^2)
```

交差相互作用も、以下のように追加のエントリを加えることでテストできます。

```julia
statistics = params -> vcat(params, params.^2, reshape(params*params',:))
```

しかし、当然のことながら、より多くの統計を追加すると、テストの計算コストが増加します。

また、異なるテストは、同じ `statistics` 関数を通じて異なる統計が計算される結果になる場合があります。たとえば、二標本テスト戦略は、モデルパラメータ `θ` とデータ `y` の両方を生成します。したがって、`params = vcat(θ, y)` となります。一方、正確な順位テストはモデルパラメータ `θ` のみを生成します。したがって、`params = θ` となります。もちろん、`statistics` はテストに使用するパラメータのサブセットを `select` するためにも使用できます。たとえば、二標本テスト戦略の場合、テストに `θ` のみを使用したい場合、`d = length(θ) > 0` のとき、次のようにできます。

```julia
statistics = params -> θ[1:d]
```
