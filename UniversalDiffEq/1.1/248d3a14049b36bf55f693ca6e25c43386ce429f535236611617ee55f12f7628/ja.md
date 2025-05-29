```
predict(UDE::BayesianUDE,test_data::DataFrame;summarize = true,ci = 95,df = true)
```

ベイジアンUDE `UDE` を使用して、トレーニングでサンプリングされた各パラメータに対してデータ `test_data` の状態を予測します。

`summarize` が `true` の場合、この関数は中央値の予測と `ci`% の下限および上限の信頼区間を返します。そうでない場合は、サンプリングされた各パラメータの個々の予測をすべて返します。

`df` が true の場合、この関数は `DataFrame` オブジェクトを返します。そうでない場合は、予測を含む `Array` を返します。
