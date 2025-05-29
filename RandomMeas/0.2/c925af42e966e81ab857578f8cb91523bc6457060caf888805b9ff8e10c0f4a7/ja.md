```
ShallowUnitaryMeasurementSetting
```

各量子ビットに対して、計算基底から測定基底への単一量子ビット回転を通じて指定される測定設定を表す構造体です。

# フィールド

  * `N::Int`: サイト数（量子ビット）。
  * 'K::Int`: shallow_unitaryを生成するゲートの数
  * `localunitary::Vector{ITensor}`: shallow unitaryを表すNgatesのベクトル
  * `site_indices::Vector{Index{Int64}}`: 長さNのサイトインデックスのベクトル。

# コンストラクタ

次の条件を検証した後に`ShallowUnitaryMeasurementSetting`オブジェクトを作成します：

  * `local_unitary`の長さが`K`に等しい
  * `site_indices`の長さが`N`に等しい。
