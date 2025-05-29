```
XPRSchgobjsense(prob, objsense)::prob
```

問題の目的関数の感覚を最小化または最大化に変更します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objsense::XPRSObjSense`: 最小化に変更するための `XPRS_OBJ_MINIMIZE`、または最大化問題に変更するための `XPRS_OBJ_MAXIMIZE`。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSchgobjsense](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgobjsense.html)。
