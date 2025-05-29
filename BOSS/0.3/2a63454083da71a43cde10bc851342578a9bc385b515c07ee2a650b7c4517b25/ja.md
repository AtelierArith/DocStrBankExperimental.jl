`BossOptions`に`BossCallback`が提供されると、コールバックはBO手続きが開始される前と各イテレーションの後に1回呼び出されます。

すべてのコールバックは次のように実装する必要があります：

  * (::CustomCallback)(::BossProblem;       ::ModelFitter,       ::AcquisitionMaximizer,       ::AcquisitionFunction,       ::TermCond,       ::BossOptions,       first::Bool,   )

キーワード引数`first`は、BO手続きが開始される前の最初のコールバックでのみtrueになります。

プロット用のコールバックの使用例については`PlotCallback`を参照してください。
