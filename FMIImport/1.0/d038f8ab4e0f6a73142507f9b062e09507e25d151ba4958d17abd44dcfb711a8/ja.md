```
fmi3EvaluateDiscreteStates(c::FMU3Instance)
```

この関数は、前の値から離散状態の現在の値を計算するために fdisc の評価をトリガーするために呼び出されます。FMU は、fmi3EvaluateDiscreteStates のサポートを capability flag providesEvaluateDiscreteStates を介して示します。

# 引数

  * `c::FMU3Instance`: ミュータブル構造体で、FMI 3.0 標準の FMU のインスタンス化されたインスタンスを表します。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi3OK`: すべて正常
  * `fmi3Warning`: いくつかの問題があるが、計算は続行できる
  * `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合
  * `fmi3Error`: 通信ステップを全く実行できなかった場合
  * `fmi3Fatal`: FMU を不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.3. 状態: 初期化モード

また、[`fmi3EvaluateDiscreteStates`](@ref) も参照してください。
