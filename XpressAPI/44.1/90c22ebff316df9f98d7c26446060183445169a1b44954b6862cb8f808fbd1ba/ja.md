```
XPRStunerreadmethod(prob, methodfile)::prob
```

この関数は、指定されたファイルからユーザー定義のチューナーメソッドをロードします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `methodfile::Union{Nothing,AbstractString}`: チューナーがユーザー定義のチューナーメソッドをロードできるメソッドファイル名。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRStunerreadmethod](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStunerreadmethod.html)。
