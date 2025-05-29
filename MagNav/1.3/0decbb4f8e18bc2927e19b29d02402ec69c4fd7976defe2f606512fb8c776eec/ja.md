```
LinCompParams <: CompParams
```

線形空中磁気補償パラメータ構造体。`CompParams`のサブタイプです。

デフォルトのパラメータを確認するには、`LinCompParams()`と入力してください。

**一般パラメータ:**

| **パラメータ**          | **型**            | **説明**                                                                                                                                                             |
|:------------------ |:---------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `version`          | VersionNumber    | この構造体を生成するために使用されたMagNav.jlのバージョン                                                                                                                                  |
| `features_setup`   | Vector{`Symbol`} | 含める特徴のベクター、`model_type = :elasticnet, :plsr`のみに使用されます                                                                                                              |
| `features_no_norm` | Vector{`Symbol`} | 正規化しない特徴のベクター、`model_type = :elasticnet, :plsr`のみに使用されます                                                                                                           |
| `model_type`       | Symbol           | 空中磁気補償モデルのタイプ（`下記参照`）                                                                                                                                              |
| `y_type`           | Symbol           | `y`ターゲットタイプ（`下記参照`）                                                                                                                                                |
| `use_mag`          | Symbol           | `y`ターゲットベクターに使用する補償されていないスカラー磁力計 {`:mag_1_uc` など}、`y_type = :c, :d, :e`のみに使用されます                                                                                   |
| `use_vec`          | Symbol           | "外部"トレス・ローソン`A`行列に使用するベクターマグネトメーター（フラックスゲート） {`:flux_a` など}、`model_type = :TL, :mod_TL, :map_TL`のみに使用されます                                                          |
| `data_norms`       | Tuple            | データ正規化の長さ`4`のタプル、`(A_bias,A_scale,y_bias,y_scale)`は`model_type = :TL, :mod_TL, :map_TL`用、または`(x_bias,x_scale,y_bias,y_scale)`は`model_type = :elasticnet, :plsr`用です |
| `model`            | Tuple            | 線形モデル係数                                                                                                                                                            |
| `terms`            | Vector{`Symbol`} | トレス・ローソン`A`行列（または行列）内で使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`}、`model_type = :elasticnet, :plsr`のみに使用されます                                                   |
| `terms_A`          | Vector{`Symbol`} | "外部"トレス・ローソン`A`行列に使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}、`model_type = :TL, :mod_TL, :map_TL`のみに使用されます                                            |
| `sub_diurnal`      | Bool             | trueの場合、スカラー磁力計測定から日変化を引きます                                                                                                                                        |
| `sub_igrf`         | Bool             | trueの場合、スカラー磁力計測定からIGRFを引きます                                                                                                                                       |
| `bpf_mag`          | Bool             | trueの場合、`x`データ行列内のスカラー磁力計測定をバンドパスフィルタリングします、`model_type = :elasticnet, :plsr`のみに使用されます                                                                             |
| `reorient_vec`     | Bool             | trueの場合、ベクターマグネトメーター（フラックスゲート）をボディフレームに合わせます                                                                                                                       |
| `norm_type_A`      | Symbol           | "外部"トレス・ローソン`A`行列の正規化、`model_type = :TL, :mod_TL, :map_TL`のみに使用されます（`下記参照`）                                                                                        |
| `norm_type_x`      | Symbol           | `x`データ行列の正規化、`model_type = :elasticnet, :plsr`のみに使用されます（`下記参照`）                                                                                                    |
| `norm_type_y`      | Symbol           | `y`ターゲットベクターの正規化（`下記参照`）                                                                                                                                           |

  * `model_type`オプション:

      * `:TL`         = 古典的トレス・ローソン
      * `:mod_TL`     = 修正トレス・ローソン
      * `:map_TL`     = マップベースのトレス・ローソン
      * `:elasticnet` = 弾性ネット（リッジ回帰および/またはラッソ）
      * `:plsr`:      = 部分最小二乗回帰（PLSR）
  * `y_type`オプション:

      * `:a` = 異常場 #1、補償されたテールスティンガーのトータルフィールドスカラー磁力計測定
      * `:b` = 異常場 #2、補間された`磁気異常マップ`の値
      * `:c` = 航空機場 #1、補償されていないキャビンのトータルフィールドスカラー磁力計測定と補間された`磁気異常マップ`の値の差
      * `:d` = 航空機場 #2、補償されていないキャビンと補償されたテールスティンガーのトータルフィールドスカラー磁力計測定の差
      * `:e` = BPF'dトータルフィールド、バンドパスフィルタリングされた補償されていないキャビンのトータルフィールドスカラー磁力計測定
  * `norm_type`オプション:

      * `:standardize` = Zスコア正規化
      * `:normalize`   = 最小-最大正規化
      * `:scale`       = 最大絶対値でスケール、バイアス = 0
      * `:none`        = 1でスケール、バイアス = 0

**線形モデル特有のパラメータ:**

| **パラメータ** | **型**   | **説明**                                                 |
|:--------- |:------- |:------------------------------------------------------ |
| `k_plsr`  | Int64   | コンポーネントの数、`model_type = :plsr`のみに使用されます                |
| `λ_TL`    | Float64 | リッジパラメータ、`model_type = :TL, :mod_TL, :map_TL`のみに使用されます |
