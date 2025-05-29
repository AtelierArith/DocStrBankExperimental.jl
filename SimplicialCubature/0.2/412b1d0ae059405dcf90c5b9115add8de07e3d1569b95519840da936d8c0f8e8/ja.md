```
integrateOnSimplex(f, S; dim, maxEvals, absError, tol, rule, info, fkwargs...)
```

1つ以上の単体上での関数の積分。

# 引数

  * `f`: 積分される関数; 実スカラー値または実ベクトルを返す必要があります
  * `S`: 単体または単体のベクトル; 単体は次元nのn+1ベクトルによって与えられます
  * `dim`: `f`の成分数
  * `maxEvals`: `f`への最大呼び出し回数
  * `absError`: 要求される絶対誤差
  * `tol`: 要求される相対誤差
  * `rule`: 積分ルール、1から4の間の整数; 2*rule+1次の積分ルールが使用されます
  * `info`: ブール値、より多くの情報を印刷するかどうか
  * `fkwargs`: `f`のキーワード引数
