Brentの方法を使用して、xaとxbの間に存在することが知られている関数の根を見つけます。根は、その精度がtolになるまで更新されます。funcは解決する関数の名前です。変数rootは関数の根として返されます。評価される関数は次の定義文を持っています：

`function [fx] = func (physcon, forcvar, surfvar, x)`

関数funcはxで評価され、返される値はfxです。これはphyscon、forcvar、surfvar、およびfluxvar構造体の変数を使用します。これらは入力引数として渡されます。また、fluxvar構造体の変数の値も計算するため、これは関数呼び出しの出力引数として返す必要があります。Julia関数`func`はfuncを評価します。

# 入力

  * `args...`: funcに渡される他の引数
