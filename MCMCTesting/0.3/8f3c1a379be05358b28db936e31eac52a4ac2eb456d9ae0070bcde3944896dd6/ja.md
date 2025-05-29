```
simulate_ranks([rng,] test, subject; kwargs...)
```

正確な順位テスト戦略に従って順位をシミュレートします。

# 引数

  * `rng::Random.AbstractRNG`: 擬似乱数生成器。 (デフォルト: `Random.default_rng()`.)
  * `test::AbstractMCMCTest`: テスト戦略。
  * `subject::TestSubject`: テスト対象のMCMCアルゴリズムとモデル。

# キーワード引数

  * `tie_epsilon::Real`: 統計の差をタイと宣言するための許容範囲。 (デフォルト: `eps(Float32)`.)
  * `statistics`: テストから生成されたサンプルからテスト統計を計算するための関数。 (追加の説明については以下のセクションを参照。)
  * `show_progress::Bool`: 進行状況を表示するかどうか。

# 戻り値

  * ranks::Matrix: シミュレートされた順位。各行は各統計の順位サンプルです。
