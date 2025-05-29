```
pvalue(lrt::LikelihoodRatioTest)
```

尤度比検定に関連するp値を抽出します。

2つ以上のモデルを含む`LikelihoodRatioTest`の場合、どのp値が必要か不明なため、エラーが発生します。

複数の検定のp値を取得するには、`lrt.pvalues`を使用してください。
