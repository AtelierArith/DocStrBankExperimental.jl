```
XPRScrossoverlpsol(prob)::status
```

与えられたLP問題の解に対する基本的な最適解を提供します。

この関数は、バリアアルゴリズムの後のクロスオーバーのように動作します。

# 引数

  * `prob::XPRSprob`: 現在の問題。

# 戻り値

  * `status::Int32`: ステータスが返される`int`へのポインタ。

対応する関数のドキュメント[XPRScrossoverlpsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScrossoverlpsol.html)をC APIで参照してください。
