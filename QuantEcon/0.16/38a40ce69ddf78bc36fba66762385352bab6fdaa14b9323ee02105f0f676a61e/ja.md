与えられたポリシー `sigma` に対する制御マルコフ連鎖を返します。

##### パラメータ

  * `ddp::DiscreteDP` : モデルパラメータを含むオブジェクト
  * `ddpr::DPSolveResult` : 結果変数を含むオブジェクト

##### 戻り値

mc : MarkovChain      制御マルコフ連鎖。
