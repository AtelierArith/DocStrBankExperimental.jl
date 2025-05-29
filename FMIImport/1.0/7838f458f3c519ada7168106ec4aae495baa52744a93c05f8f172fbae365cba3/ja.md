```
fmi3EnterInitializationMode(c::FMU3Instance, toleranceDefined::fmi3Boolean,
    tolerance::fmi3Float64,
    startTime::fmi3Float64,
    stopTimeDefined::fmi3Boolean,
    stopTime::fmi3Float64)
```

FMUに初期化モードに入るように指示します。この関数を呼び出す前に、属性が<Datatype initial = "exact" or "approx">のすべての変数は「fmi3SetXXX」関数を使用して設定できます（スカラー変数の属性はモデル記述ファイルで定義されています。セクション2.4.7を参照）。他の変数を設定することは許可されていません。また、シミュレーションの開始時刻と停止時刻も設定します。

# 引数

  * `c::FMU3Instance`: 引数`c`は、FMI 3.0標準のFMUのインスタンス化されたインスタンスを表す可変構造体です。
  * `toleranceDefined::fmi3Boolean`: 引数`toleranceDefined`はFMUのタイプに依存します：

      * fmuType = fmi3ModelExchange: `toleranceDefined = fmi3True`の場合、モデルは数値積分スキームで呼び出され、ステップサイズは誤差推定のために`tolerance`を使用して制御されます。この場合、モデル内で使用されるすべての数値アルゴリズム（例えば、非線形代数方程式を解くためのもの）は、適切な小さい相対誤差の推定で動作する必要があります。
      * fmuType = fmi3CoSimulation: `toleranceDefined = fmi3True`の場合、スレーブの通信間隔は誤差推定によって制御されます。スレーブが可変ステップサイズと誤差推定を持つ数値積分器を利用する場合、内部積分器の誤差推定に「tolerance」を使用することが推奨されます（通常は相対誤差として）。コシミュレーション用のFMUはこの引数を無視する場合があります。
  * `tolerance::fmi3Float64`: 引数`tolerance`は、希望する許容誤差です。
  * `startTime::fmi3Float64`: 引数`startTime`は、モデルが与えられた境界内で有効かどうかを確認するため、または結果を保存するために必要なメモリを割り当てるために使用できます。これは独立変数の固定初期値であり、独立変数が`time`の場合、`startTime`は初期化の開始時刻です。
  * `stopTimeDefined::fmi3Boolean`: `stopTimeDefined = fmi3True`の場合、stopTimeは独立変数の定義された最終値であり、`stopTimeDefined = fmi3False`の場合、独立変数の最終値は定義されておらず、引数`stopTime`は無意味です。
  * `stopTime::fmi3Float64`: 引数`stopTime`は、モデルが与えられた境界内で有効かどうかを確認するため、または結果を保存するために必要なメモリを割り当てるために使用できます。これは独立変数の固定最終値であり、独立変数が「time」の場合、stopTimeはシミュレーションの停止時刻です。

# 戻り値

  * `status::fmi3Status`: 戻り値`status`は`fmi3Status`型の列挙であり、関数呼び出しの成功を示します。

詳細は次のとおりです：     - `fmi3OK`: すべて正常     - `fmi3Warning`: 物事は完全ではありませんが、計算を続けることができます     - `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合     - `fmi3Error`: 通信ステップを全く実行できなかった場合     - `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.2. 状態: インスタンス化された

[`fmi3EnterInitializationMode`](@ref)も参照してください。
