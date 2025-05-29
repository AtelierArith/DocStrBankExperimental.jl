```
inpolygon(p, poly)
inpolygon(p, poly, [::MembershipCheckAlgorithm])
inpolygon(p, poly, [::MembershipCheckAlgorithm]; in = 1, on = -1, out = 0)
```

`poly`が`AbstractVector`の`AbstractVector`であるとき、`p`が`poly`に属しているかを確認します。`poly`の最初と最後の要素は等しくする必要があります。

*戻り値:*

  * in = 1
  * on = -1
  * out = 0

*MembershipCheckAlgorithm:*

  * `HaoSun()`
  * `HormannAgathos()`

デフォルトは`HaoSun()`で、これは最良のパフォーマンスを持ち、巻き順や自己交差に依存しません。ただし、HaoSunアルゴリズムは新しいため、バグが発生する可能性があります。古典的なHormannAgathosアルゴリズムも提供されていますが、これは自己交差や巻き順に敏感であり、異なる結果を生成する可能性があります。

*カスタム戻り値:*

戻り値のロジックは、`in`、`on`、および`out`キーワードを指定することで、代替の値や型を返すようにカスタマイズできます。たとえば、'on'と'in'のケースを同じと見なし、`Bool`を返すには: `inpolygon(p, poly, in=true, on=true, out=false)`

HaoとSunによるアルゴリズム (2018): https://doi.org/10.3390/sym10100477

Hormann-Agathos (2001) ポイントインポリゴンアルゴリズム: https://doi.org/10.1016/S0925-7721(01)00012-8
