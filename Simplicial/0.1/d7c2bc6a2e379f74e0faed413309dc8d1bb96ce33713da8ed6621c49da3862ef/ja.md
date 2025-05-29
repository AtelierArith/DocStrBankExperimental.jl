beta=BettiNumbers(D::DirectedComplex,maximaldimension=Inf) この関数は、PHATへのインターフェースを使用して、指向複体のホモロジーのベッティ数を返します。

ここで、betaの長さはmaximaldimension+1に等しく、beta[1]は0次ベッティ数であり、beta[P.dim+1]はP.dim次のベッティ数です。maximaldimensionは、計算するホモロジーの最大可能次元を制限するためのオプションのパラメータです。
