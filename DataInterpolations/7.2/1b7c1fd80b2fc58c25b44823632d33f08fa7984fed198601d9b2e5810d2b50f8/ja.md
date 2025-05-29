```
BSplineApprox(u, t, d, h, pVecType, knotVecType; extrapolation::ExtrapolationType.T = ExtrapolationType.None, extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_right::ExtrapolationType.T = ExtrapolationType.None)
```

これは回帰ベースのBスプラインです。引数の選択は`BSplineInterpolation`と同じで、追加のパラメータ`h < length(t)`は使用する制御点の数を示し、`h`が小さいほどスムージングが強くなります。詳細については、[http://www.cad.zju.edu.cn/home/zhx/GM/009/00-bsia.pdf](http://www.cad.zju.edu.cn/home/zhx/GM/009/00-bsia.pdf)を参照してください。外挿は両端の各側の定数多項式です。

## 引数

  * `u`: データポイント。
  * `t`: 時間ポイント。
  * `d`: 区分多項式の次数。
  * `h`: 使用する制御点の数。
  * `pVecType`: パラメータベクトルのシンボル、均等間隔のパラメータには`:Uniform`、弦長法で生成されたパラメータには`:ArcLen`を指定します。
  * `knotVecType`: ノットベクトルのシンボル、均等ノットベクトルには`:Uniform`、平均間隔のノットベクトルには`:Average`を指定します。

## キーワード引数

  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは`ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic`、および`ExtrapolationType.Reflective`です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは`extrapolation != Extrapolation.none`の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは`extrapolation != Extrapolation.none`の場合は無視されます。
  * `assume_linear_t`: 均等に分布したアブシッサに対してより高速なインデックスルックアップ動作を指定するためのブール値。あるいは、直線に対する差の正規化された標準偏差に基づくテストのための数値しきい値を指定することもできます（[`looks_linear`](@ref)を参照）。デフォルトは1e-2です。
