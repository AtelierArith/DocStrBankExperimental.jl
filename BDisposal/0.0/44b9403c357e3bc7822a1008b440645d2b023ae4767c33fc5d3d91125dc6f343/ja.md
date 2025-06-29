```
efficiencyScores(gI,gO,bO,bI;retToScale,prodStructure,dirGI,dirBI,dirGO,dirBO,startθ,startμ,startλ)
```

良い出力と悪い出力の結合生産を考慮した効率指標と凸性テストの結果を計算します。

異なる意思決定単位のための入力、"良い"（"望ましい"）および"悪い"（"望ましくない"）出力の測定値のセットが与えられたとき、それらの生産フロンティアへの距離、すなわち効率の度合いを計算します。

## パラメータ:

  * ポジショナル

      * `gI`: "良い"入力（DMU、入力項目、期間による3Dマトリックス）
      * `gO`: "良い"出力（DMU、入力項目、期間による3Dマトリックス）
      * `bO`: "悪い"出力（DMU、入力項目、期間による3Dマトリックス）
      * `bI`: "悪い"入力（オプションのDMU、入力項目、期間による3Dマトリックス）[デフォルト: 空の配列]
  * キーワード

      * `retToScale`: スケールの帰納が"定常"または"変動"（デフォルト）であるべきか。非凸距離とテストは、"変動"の仮定の下でのみ計算され、乗法生産関数の下での(0,0,1,-1)距離を除く
      * `prodStructure`: 生産構造が"加法的"（デフォルト）または"乗法的"であるべきか
      * `dirGI`,`dirBI`,`dirGO`,`dirBO`: 効率を測定する方向（注を参照）[デフォルト: `(0,0,1,0)`]
      * `startθ`,`startμ`,`startλ`: 凸最適化問題における初期値 [デフォルト: `(0,0,1.1)`]

## 戻り値:

  * 次の項目を持つ名前付きタプル:

      * `λs`: 凸性テストと整合する効率指標（DMUと期間による2Dマトリックス）
      * `λs_convex`: 凸生産フロンティアを仮定した効率指標（DMUと期間による2Dマトリックス）
      * `λs_nonconvex`: 非凸生産フロンティアを仮定した効率指標（DMUと期間による2Dマトリックス）
      * `nonConvTest`: 非凸性テストの結果（DMUと期間によるブールの2Dマトリックス）。ここでの"true"は非凸を指します。
      * `nonConvTest_value`: 非凸性テストの値（DMUと期間による2Dマトリックス）

## 関数の説明

`efficiencyScores`は、意思決定単位（すなわち、観察）のセットに対する環境効率指標を定義します。DMUの性質（例：企業、国など）は、環境効率分析の目的によって異なります。

すべてのDMUは、望ましくない（例：汚染）および望ましい（例：非汚染）ものに分けられた入力と出力のセットによって特徴付けられます。BDisposalパッケージにおいて、望ましい（例：排出を引き起こさない）および望ましくない（例：排出を引き起こす）成分への入力の分離はオプションであることに注意してください。

BDisposal DEAモデリングは、すべてのDMU情報（入力/出力）を含み、B-廃棄の公理的パターンを満たす最小の環境生産プロセスを定義します。

効率評価のためのBDisposalアルゴリズムは、最良の環境生産手続きへの距離を計算します。すなわち、効率的な生産フロンティアへの距離です。これらの効率指数は、加法的および乗法的距離関数の構造を引き継ぎます。

BDisposalパッケージは、加法的および乗法的距離関数の一般的な形状を計算します。したがって、BDisposalパッケージは、距離関数の異なる方向を分析する可能性を持つ環境効率評価のための柔軟なフレームワークを導入します。さらに、BDisposalパッケージは、凸性と廃棄可能性の（経済学者の）特性をテストすることを可能にします。

## 結果の解釈

### 効率指標

距離関数の加法的形状が0より大きい場合、製造単位は効率的に運営されていません。加法的効率スコアが0に等しい場合、DMUは効率的です。したがって、DMUは入力を出力に変換するための最良の生産技術の1つを使用しています。すなわち、製造者は他の観察のベンチマークです。乗法的距離関数についても同様の理由が成り立ちます。

乗法的効率指数が1より大きい場合、DMUは効率的に機能していません。乗法的効率スコアが1に等しい場合、製造単位は他の観察のベンチマークです。

### 凸性テスト

乗法的凸性テストが1より大きい場合（それぞれ、1に等しい場合）、生産プロセスのフロンティアは非凸です（それぞれ、凸です）。乗法的廃棄可能性テストが1より大きい場合（それぞれ、1に等しい場合）、生産セットのフロンティアはB-廃棄可能性を示します。すなわち、望ましくない成分の減少にコストが存在します。加法的フレームワークについても同様の理由が適用されます。

これらのテストによって提供される情報は、生産プロセスの境界の形状を定義します。

## 注:

  * 効率距離を測定する方向は、`dirGI`,`dirBI`,`dirGO`および`dirBO`パラメータを使用して調整できます。
  * 次の方向がサポートされています:

      * 乗法的生産構造: (-1,0,0,0), (0,-1,0,0), (0,0,1,0), (0,0,0,-1)または(0,0,1,-1)
      * 加法的生産構造: (1,0,0,0), (0,1,0,0), (0,0,1,0)または(0,0,0,1)

    他の方向を使用して凸フロンティア仮定の下での方向を計算できますが、凸性テストは実行されず、乗法的な場合には、基礎となる（非線形）問題の解決に保証はありません（異なる初期値`startθ`,`startμ`,`startλ`を試すことができます）
