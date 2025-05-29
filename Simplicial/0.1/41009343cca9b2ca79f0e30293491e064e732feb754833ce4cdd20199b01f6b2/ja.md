beta=BettiNumbers*naive*method(D::DirectedComplex,maximaldimension=Inf)

この関数は、（これまで純粋な）有向複体のホモロジーのベッティ数を返します。これは、有向ホモロジーを計算する非常に粗い方法です - これは、トリックを使用せず、定義と、十分に大きな行列で正しく機能しない可能性のある組み込みのランク関数のみを使用します。注意して使用してください。十分に小さな複体では、指定通りに機能します。

ここで、betaの長さはmaximaldimension+1に等しく、beta[1]は0次ベッティ数であり、beta[P.dim+1]はP.dim次のベッティ数です。maximaldimensionは、計算するホモロジーの最大可能次元を制限するためのオプションのパラメータです。
