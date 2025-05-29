```
fmi3GetAdjointDerivative(c::FMU3Instance,
    unknowns::AbstractArray{fmi3ValueReference},
    knowns::AbstractArray{fmi3ValueReference},
    seed::AbstractArray{fmi3Float64})
```

変数 `unknowns` に関する偏微分を計算するラッパー関数呼び出し。

FMU の随伴導関数を計算します。FMU には異なるモードがあり、各モードでは異なる方程式と異なる未知数で記述される場合があります。正確な定義は、モデル交換の数学的記述（セクション 3）およびコシミュレーション（セクション 4）に記載されています。各モードにおける FMU 方程式の一般的な形式は次のとおりです: unknowns = 𝐡(knowns, rest)

  * `unknowns`: 実際のモードで計算される未知の実数変数のベクトル:

      * 初期化モード: `<ModelStructure><InitialUnknown>` の下にリストされた未知数で、型は実数です。
      * 連続時間モード（モデル交換）: 連続時間出力および状態導関数。（= `<ModelStructure><Output>` の下にリストされた型が実数で変動性が `continuous` の変数および `<ModelStructure><ContinuousStateDerivative>` の下にリストされた状態導関数としての変数）。
      * イベントモード（モデル交換/コシミュレーション）: 連続時間モードと同じ変数に加えて、型が実数で変動性が `discrete` の `<ModelStructure><Output>` の下にある変数。
      * ステップモード（コシミュレーション）: 型が実数で変動性が `continuous` または `discrete` の `<ModelStructure><Output>` の下にリストされた変数。`<ModelStructure><ContinuousStateDerivative>` が存在する場合、ここに状態導関数としてリストされた変数も含まれます。
  * `knowns`: 実際のモードで値が変化する関数 h の実数入力変数。
  * `rest`: 実際のモードで値が変化するが非実数変数である関数 h の入力変数の集合、またはこのモードでは値が変化しないが他のモードでは値が変化する変数。

選択された入力変数 𝐯_known に関する h の偏微分の線形結合を計算します:

Δunknowns = (δh / δknowns) Δknowns

# 引数

  * `c::FMU3Instance` ミュータブル構造体で、FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表します。
  * `unknowns::AbstracArray{fmi3ValueReference}`: 引数 `unknowns` には、モデルの変数値の識別子である `fmi3ValueReference` 型の値が含まれています。`unknowns` は上記の `unknowns`（変数）と等価です。
  * `knowns::AbstractArray{fmi3ValueReference}`: 引数 `knowns` には、モデルの変数値の識別子である `fmi3ValueReference` 型の値が含まれています。`knowns` は上記の `knowns`（変数）と等価です。
  * `seed::AbstractArray{fmi3Float64}`: ベクトル値は、`knowns` のベクトル内の指定されたエントリに関する偏微分を計算し、`sensitivity` の一致する評価を行います。

# 戻り値

  * `sensitivity::Array{fmi3Float64}`: 戻り値 `sensitivity` には、方向導関数ベクトル値が含まれます。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.11. 偏微分の取得

[`fmi3GetAdjointDerivative`](@ref) も参照してください。 ```
