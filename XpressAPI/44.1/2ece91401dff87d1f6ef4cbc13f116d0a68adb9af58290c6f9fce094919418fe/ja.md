```
XPRStune(prob, flags)::prob
```

この関数は、現在の問題のためのチューナーセッションを開始します。

チューナーは、制御設定のリストとそれらの有望な組み合わせを評価しながら、問題を複数回解決します。終了すると、チューナーは問題に最適な制御設定を選択して設定します。最適化の方向はOBJSENSEによって示されることに注意してください。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `flags::Union{Nothing,AbstractString}`: 現在の問題をLPまたはMIP問題としてチューニングするかどうか、LP問題を解決するためのアルゴリズムまたはMIPの初期LP緩和を指定するためにXPRStuneに渡すフラグ。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRStune](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStune.html)のドキュメントも参照してください。
