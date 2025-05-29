```
struct LikelihoodRatioTest <: GoodnessOfFit end
const LRT = LikelihoodRatioTest
```

尤度比検定によるANOVA。最初の引数またはキーワード引数 `test` で指定できます。
