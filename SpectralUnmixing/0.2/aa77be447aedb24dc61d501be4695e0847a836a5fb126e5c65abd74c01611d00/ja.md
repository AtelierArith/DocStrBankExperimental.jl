```
simulate_pixel(library::SpectralLibrary, max_components::Int64,
                combination_type::String, seed::Int64)
```

ライブラリ内のエンドメンバーのランダム正規化分布からピクセルの反射データをシミュレートします。

# 引数

  * `library::SpectralLibrary`: エンドメンバーとクラス情報を含むスペクトルライブラリ。
  * `max_components::Int64`: シミュレーションに使用するエンドメンバーの最大数。
  * `combination_type::String`: エンドメンバーを選択する際に考慮する組み合わせのタイプ（例："all" または "class-even"）。
  * `seed::Int64`: ランダム数生成器のシード。

# 戻り値

  * 次の内容を含むタプル：

      * `simulated_rfl`: ピクセルのシミュレートされた反射スペクトル。
      * `output_distribution`: ピクセルのエンドメンバーの寄与のベクトル。
      * `output_distribution_classes`: 各ユニーククラスの寄与のベクトル。
