LQタイプのメインコンストラクタ

ペイオフ関数や遷移方程式の一部でないすべてのフィールドのデフォルト引数を指定します。

##### 引数

  * `Q::ScalarOrArray` : 制御変数uのための`k x k`ペイオフ係数。対称で非負定義でなければなりません。
  * `R::ScalarOrArray` : 状態変数xのための`n x n`ペイオフ係数行列。対称で非負定義でなければなりません。
  * `A::ScalarOrArray` : 状態遷移における状態の`n x n`係数。
  * `B::ScalarOrArray` : 状態遷移における制御の`n x k`係数。
  * `;C::ScalarOrArray{zero(size(R}(1)))` : 状態遷移におけるランダムショックの`n x j`係数。
  * `;N::ScalarOrArray{zero(size(B,1)}(size(A, 2)))` : ペイオフ方程式における`k x n`クロスプロダクト。
  * `;bet::Real(1.0)` : `[0, 1]`の範囲の割引因子。
  * `capT::Union{Int, Void}(Void)` : 有限ホライズン問題における終端期間。
  * `rf::ScalarOrArray{fill(NaN}(size(R)...))` : 有限ホライズン問題における`n x n`終端ペイオフ。対称で非負定義でなければなりません。
