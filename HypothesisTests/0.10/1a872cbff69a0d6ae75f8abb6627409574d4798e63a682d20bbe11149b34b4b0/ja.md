```
pvalue(test::HypothesisTest; tail = :both)
```

与えられた有意性検定のp値を計算します。

`tail`が`:both`（デフォルト）の場合、二項検定のp値が返されます。`tail`が`:left`または`:right`の場合は、一方の検定が実行されます。
