```
fmiGetDirectionalDerivative!(c::FMU2Component,
                                  vUnknown_ref::AbstractArray{fmi2ValueReference},
                                  vKnown_ref::AbstractArray{fmi2ValueReference},
                                  dvKnown::Array{fmi2Real},
                                  dvUnknown::AbstractArray)
```

変数 `vKnown_ref` に関する偏微分を計算するラッパー関数呼び出し。

FMU の方向微分を計算します。FMU には異なるモードがあり、各モードでは FMU が異なる方程式と異なる未知数で記述される場合があります。正確な定義は、モデル交換の数学的記述（セクション 3.1）およびコシミュレーション（セクション 4.1）に記載されています。各モードにおいて、FMU 方程式の一般的な形式は次のとおりです： 𝐯*unknown = 𝐡(𝐯*known, 𝐯_rest)

  * `v_unknown`: 実際のモードで計算された未知の実数変数のベクトル：

      * 初期化モード：タイプが Real の `<ModelStructure><InitialUnknowns>` にリストされた未知数。
      * 連続時間モード（モデル交換）：連続時間出力および状態微分。（= `<ModelStructure><Outputs>` にリストされたタイプが Real で変動性が `continuous` の変数および `<ModelStructure><Derivatives>` にリストされた状態微分としての変数）。
      * イベントモード（モデル交換）：連続時間モードと同じ変数に加えて、タイプが Real で変動性が `discrete` の `<ModelStructure><Outputs>` にリストされた変数。
      * ステップモード（コシミュレーション）：タイプが Real で変動性が `continuous` または `discrete` の `<ModelStructure><Outputs>` にリストされた変数。`<ModelStructure><Derivatives>` が存在する場合、ここにリストされた状態微分としての変数も含まれます。
  * `v_known`: 実際のモードでその値が変化する関数 h の実数入力変数。
  * `v_rest`: 実際のモードでその値が変化するが非実数変数である関数 h の入力変数のセット、またはこのモードでは値が変化しないが他のモードでは値が変化する変数。

選択された入力変数 𝐯_known に関する h の偏微分の線形結合を計算します：

```
Δv_unknown = (δh / δv_known) Δv_known
```

# 引数

  * `c::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンスを表す可変構造体。
  * `vUnknown_ref::AbstracArray{fmi2ValueReference}`: 引数 `vUnknown_ref` には、モデルの変数値の識別子である `fmi2ValueReference` 型の値が含まれています。`vUnknown_ref` は上記の変数 `v_unknown` と等価です。
  * `vKnown_ref::AbstractArray{fmi2ValueReference}`: 引数 `vKnown_ref` には、モデルの変数値の識別子である `fmi2ValueReference` 型の値が含まれています。`vKnown_ref` は上記の変数 `v_known` と等価です。
  * `dvUnknown::AbstractArray{fmi2Real}`: 方向微分ベクトル値を格納します。
  * `dvKnown::Union{AbstractArray{fmi2Real}, Nothing} = nothing`: シードベクトルが渡されない場合、値 `nothing` が使用されます。ベクトル値は、`vKnown_ref` の指定されたエントリに関する偏微分を計算し、`dvKnown` の一致する評価を行います。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙であり、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが非同期に関数を実行する場合にこのステータスが返されます

# ソース

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.25]: 2.1.9 偏微分の取得

[`fmi2GetDirectionalDerivative!`](@ref) も参照してください。 ```
