```
struct LikelihoodRatioTest <: GoodnessOfFit end
const LRT = LikelihoodRatioTest
```

タイプは、尤度比検定によるANOVAの実施を示します。最初の引数またはキーワード引数 `test` で指定できます。
