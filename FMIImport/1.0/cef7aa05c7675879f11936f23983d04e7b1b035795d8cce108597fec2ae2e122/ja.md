```
fmi2GetStatus!(c::FMU2Component, 
                    s::fmi2StatusKind, 
                    value::Ref{fmi2Status})
```

シミュレーション実行の実際のステータスについてマスターに通知します。どのステータス情報を返すかは、引数 `fmi2StatusKind` で指定されます。

# 引数

  * `c::FMU2Component`: FMI 2.0.2 標準における FMU のインスタンス化されたインスタンスを表す可変構造体。
  * `s::fmi2StatusKind`: 引数 `s` は、どのステータス情報を返すかを定義します。`fmi2StatusKind` は、どのステータスが問い合わせられるかを定義する列挙型です。

スレーブから取得できるステータス情報は以下の通りです：

  * `fmi2DoStepStatus::fmi2Status`: `fmi2DoStep` 関数が `fmi2Pending` を返したときに呼び出すことができます。この関数は、計算が終了していない場合に `fmi2Pending` を返します。そうでない場合、この関数は非同期に実行された `fmi2DoStep` 呼び出しの結果を返します。
  * `fmi2PendingStatus::fmi2String`: `fmi2DoStep` 関数が `fmi2Pending` を返したときに呼び出すことができます。この関数は、現在実行中の非同期 `fmi2DoStep` 計算のステータスについての情報を提供する文字列を返します。
  * `fmi2LastSuccessfulTime:: fmi2Real`: 最後に成功裏に完了した通信ステップの終了時間を返します。fmi2DoStep(..) が fmi2Discard を返した後に呼び出すことができます。
  * `fmi2Terminated::fmi2Boolean`: スレーブがシミュレーションを終了したい場合、`fmi2True` を返します。fmi2DoStep(..) が `fmi2Discard` を返した後に呼び出すことができます。スレーブが終了した時点を特定するには fmi2LastSuccessfulTime を使用します。
  * `value::Ref{fmi2Status}`: `value` 引数は、要求されたステータスフラグを指します。

# 戻り値

  * `status::fmi2Status`: 戻り値 `status` は `fmi2Status` 型の列挙型で、関数呼び出しの成功を示します。

より詳細には：

  * `fmi2OK`: すべて正常
  * `fmi2Warning`: いくつかの問題があるが、計算は続行可能
  * `fmi2Discard`: スレーブが通信ステップのサブインターバルのみを成功裏に計算した場合
  * `fmi2Error`: 通信ステップを全く実行できなかった場合
  * `fmi2Fatal`: FMU を不可逆的に破損させるエラーが発生した場合
  * `fmi2Pending`: スレーブが関数を非同期に実行している場合にこのステータスが返されます

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.106]: 4.2.3 スレーブからのステータス情報の取得

また、[`fmi2GetStatus!`](@ref) も参照してください。
