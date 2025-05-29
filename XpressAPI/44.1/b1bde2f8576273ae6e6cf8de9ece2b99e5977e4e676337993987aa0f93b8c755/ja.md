```
XPRSgetstrattrib(prob, attrib)::value
```

ユーザーがさまざまな文字列問題属性の値を回復できるようにします。

問題属性は、問題の読み込みと最適化中に設定されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `attrib::Integer`: 値を返す問題属性。

# 戻り値

  * `value::AbstractString`: 属性の値（およびヌル終端子）のポインタが返されます。

C APIの対応する関数のドキュメントも参照してください [XPRSgetstrattrib](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstrattrib.html)。
