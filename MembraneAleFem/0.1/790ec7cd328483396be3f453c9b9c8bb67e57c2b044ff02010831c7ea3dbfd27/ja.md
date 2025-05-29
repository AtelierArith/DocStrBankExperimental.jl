```
Params
```

シミュレーションに指定する必要があるパラメータ。

[`Scenario`](@ref)固有のデータで、キーワード引数を介して含める必要があるものについては、[`check_params`](@ref MembraneAleFem.check_params)を参照してください。以下の情報が含まれています：

  * `motion::`[`Motion`](@ref)     → 動きのタイプ
  * `scenario::`[`Scenario`](@ref) → シナリオのタイプ
  * `num1el::Int64`   → $ζ^1$の要素数
  * `num2el::Int64`   → $ζ^2$の要素数
  * `output::Bool`    → 出力を書く（デフォルトでははい）
  * `length::Float64` → 実空間での長さ
  * `kb::Float64`     → 平均曲げ剛性
  * `kg::Float64`     → ガウス曲げ剛性
  * `ζv::Float64`     → 膜の粘度
  * `pn::Float64`     → 法線圧力（体積力）
  * `poly::Int64`     → 基底関数の多項式次数
  * `gp1d::Int64`     → 1次元のガウスポイントの数
  * `nders::Int64`    → 1次元Bスプラインの導関数の数
  * `nen::Int64`      → 要素ノードの数
  * `αdb::Float64`    → ドールマン–ボチェフパラメータ
  * `αm::Float64`     → メッシュパラメータ
  * `εk::Float64`     → 行列Kの数値計算の許容誤差
  * `εnr::Float64`    → ニュートン–ラフソンの許容誤差
