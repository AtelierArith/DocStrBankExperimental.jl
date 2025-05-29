```
prodIndexFB(gI,gO,bO,bI;remarcable_obs_dmu,remarcable_obs_period)
```

固定基準で生産性指数を計算します。

異なる意思決定単位に対する「良い」("desiderable")および「悪い」("undesiderable")出力の入力の測定値のセットと、基準として考慮する特定のdmu/時間観測（「remarkable」）を考慮して、さまざまな時間期間における生産性指数を提供します。

## パラメータ:

  * 位置引数

      * `gI`: 「良い」入力（DMU、入力項目、期間による3D配列）
      * `gO`: 「良い」出力（DMU、入力項目、期間による3D配列）
      * `bO`: 「悪い」出力（DMU、入力項目、期間による3D配列）
      * `bI`: 「悪い」入力（オプションのDMU、入力項目、期間による3D配列） [デフォルト: 空の配列]
  * キーワード

      * `remarcable_obs_dmu`: 「remarkable」と考慮する観測 [デフォルト: `1`]
      * `remarcable_obs_period`: 「remarkable」と考慮する期間のタイプ [デフォルト: `1`]

## 戻り値:

  * 各要素がDMUおよび時間期間による基準関連の生産指数の行列である名前付きタプル。
  * 現在報告されている値は:

      * `prodIndexes`:          全体の生産指数

## 関数の説明

`prodIndexFB`は、乗法的`prodIndex`関数の固定基準バージョンです。その結果、`prodIndexFB`は、空間的および/または時間的観測を比較するための固定基準観測の特定に基づいています。具体的には、比較のための基準観測の選択は、注目すべき空間的および/または時間的単位の特定によって影響を受けます。

## 結果の解釈

`prodIndexFB` > 1は、環境調整されたパフォーマンスの改善を示します。この場合、remarkable観測は、与えられた良いおよび悪い入力のレベルに対して、比較観測よりも多くの良い出力と少ない悪い出力を生産します。同時に、remarkable観測は、与えられた良いおよび悪い出力に対して、比較観測に比べて少ない良いおよび悪い入力を使用します。もし`prodIndexFB < 1`であれば、逆の理由が成り立ちます。

## 例

```Julia
julia> using BDisposal
julia> # 2 DMUs, 2 good Inputs, 2 bad inputs, 3 good outputs and 2 bad outputs. 2 periods
       gI = [1; 3; 5;; 2; 4; 5;;; 1; 4; 5;; 2; 5; 5];
julia> bI = [2; 4; 2;; 3; 7; 5;;; 2; 3; 2;; 3; 6; 5];
julia> gO = [10; 30; 50;; 20; 40; 50;; 15; 8; 12;;; 12; 40; 50;; 22; 50; 50;; 16; 55; 55];
julia> bO = [2; 4; 2;; 3; 7; 5;;; 2; 3; 2;; 3; 6; 5];
julia> analysis = prodIndexFB(gI,gO,bO,bI;remarcable_obs_dmu=1, remarcable_obs_period=2);
julia> analysis.prodIndexes
3×2 Matrix{Union{Missing, Float64}}:
 0.909091  1.0
 3.63636   2.33766
 1.2987    1.2987
```

## 注意:

  * この関数は、可変規模に対する凸型の乗法的生産関数を仮定しています。

```
