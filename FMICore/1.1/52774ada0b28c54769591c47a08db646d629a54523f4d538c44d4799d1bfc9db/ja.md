ソース: FMISpec2.0.2[p.18]: 2.1.3 関数によって返されるステータス

関数によって返されるステータス。ステータスは以下の意味を持ちます：

  * fmi2OK – すべて正常
  * fmi2Warning – 物事は完全ではありませんが、計算を続けることができます。モデル内で「logger」関数が呼び出され（下記参照）、この関数がユーザーに準備された情報メッセージを表示したと期待されています。
  * fmi2Discard – この返却ステータスは、対応する関数のために明示的に定義されている場合にのみ可能です。

（モデル交換: fmi2SetReal, fmi2SetInteger, fmi2SetBoolean, fmi2SetString, fmi2SetContinuousStates, fmi2GetReal, fmi2GetDerivatives, fmi2GetContinuousStates, fmi2GetEventIndicators; コシミュレーション: fmi2SetReal, fmi2SetInteger, fmi2SetBoolean, fmi2SetString, fmi2DoStep, fmiGetXXXStatus）: 「モデル交換」について: より小さなステップサイズを実行し、モデル方程式を再評価することが推奨されます。たとえば、モデル内の反復ソルバーが収束しなかった場合や、関数がその定義域の外にある場合（たとえば sqrt(<負の数>））です。これが不可能な場合、シミュレーションは終了しなければなりません。「コシミュレーション」について: スレーブが必要なステータス情報を返すことができない場合も fmi2Discard が返されます。マスターはシミュレーションを続行できるかどうかを判断しなければなりません。いずれの場合も、FMU内で「logger」関数が呼び出され（下記参照）、FMUがデバッグモードで呼び出された場合（loggingOn = fmi2True）、この関数がユーザーに準備された情報メッセージを表示したと期待されています。そうでない場合、「logger」はメッセージを表示すべきではありません。

  * fmi2Error – FMUがエラーに遭遇しました。このFMUインスタンスでシミュレーションを続行することはできません。関数のいずれかが fmi2Error を返す場合、fmi2SetFMUstate を呼び出すことで以前に保存されたFMU状態からシミュレーションを再起動することが試みられます。

この操作は、能力フラグ canGetAndSetFMUstate が true であり、fmi2GetFMUstate が非エラー状態で以前に呼び出されていた場合に行うことができます。そうでない場合、シミュレーションは続行できず、fmi2FreeInstance または fmi2Reset をその後に呼び出さなければなりません。4 この呼び出しの後にさらなる処理が可能です。特に他のFMUインスタンスには影響しません。FMU内で「logger」関数が呼び出され（下記参照）、この関数がユーザーに準備された情報メッセージを表示したと期待されています。

  * fmi2Fatal – モデル計算はすべてのFMUインスタンスに対して修復不可能に破損しています。[たとえば、fmi関数の実行中にアクセス違反やゼロによる整数除算などのランタイム例外によるものです。] FMU内で「logger」関数が呼び出され（下記参照）、この関数がユーザーに準備された情報メッセージを表示したと期待されています。いかなるFMUインスタンスに対しても他の関数を呼び出すことはできません。
  * fmi2Pending – このステータスは、スレーブが非同期的に関数を実行する場合にのみコシミュレーションインターフェースから返されます。つまり、スレーブは計算を開始しますが、すぐに返します。マスターは fmi2GetStatus(..., fmi2DoStepStatus) を呼び出して、スレーブが計算を終了したかどうかを判断しなければなりません。これは fmi2DoStep と fmi2GetStatus のみから返されることができます（セクション 4.2.3 を参照）。
