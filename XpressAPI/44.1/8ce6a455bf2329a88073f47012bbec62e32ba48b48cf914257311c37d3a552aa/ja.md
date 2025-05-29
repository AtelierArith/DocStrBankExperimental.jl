```
XPRSfixmipentities(prob, options)::prob
```

すべてのMIPエンティティを最後に見つかったMIPソリューションの値に固定します。

これは、整数変数が最適値に固定された後の連続変数の削減コストを見つけるのに役立ちます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `options::Integer`: MIPエンティティを固定する方法に関するオプション。0は、すべてのMIPエンティティを解の最も近い離散値に丸めてから固定する場合。1は、非凸の決定（すなわち、非凸の区分線形関数のどの部分またはどの変数が最大値を取るか）のみを固定し、区分線形および一般的な制約を問題に保持する場合。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSfixmipentities](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSfixmipentities.html)のドキュメントも参照してください。
