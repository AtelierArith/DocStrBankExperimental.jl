関数の根をセカント法とブレント法を使用して初期推定値xaとxbから求めます。根はその精度がtolになるまで更新されます。funcは解くべき関数の名前です。変数rootは関数の根として返されます。評価される関数は次の定義文を持っています：

function [fx] = func (physcon, forcvar, surfvar, x)

関数funcはxで評価され、返される値はfxです。これはphyscon、forcvar、surfvar、およびfluxvar構造体の変数を使用します。これらは入力引数として渡されます。また、fluxvar構造体内の変数の値も計算するため、これは関数呼び出しの出力引数として返される必要があります。Julia関数`func`はfuncを評価します。

# 入力

  * `args...`: `func`に渡される他の引数
  * `tol`: xの精度許容範囲
