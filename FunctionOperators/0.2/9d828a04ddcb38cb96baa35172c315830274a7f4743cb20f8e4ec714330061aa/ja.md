`FunctionOperators`ライブラリのグローバル設定を保持するオブジェクト

フィールド:

  * `verbose::Bool` trueに設定されている場合、割り当て情報と計算されたプラン関数が作成時（すなわち、合成演算子が初めて使用されるとき）に表示されます。デフォルト: `false`
  * `macro_verbose::Bool` trueに設定されている場合、リサイクルマクロ（@♻および@recycle）が変換されたコードを印刷します。デフォルト: `false`
  * `auto_reshape::Bool` trueに設定されている場合、入力と出力は、乗算の前後でFunctionOperatorのinDimsおよびoutDimsの値に従って再形成されます。デフォルト: `false`
