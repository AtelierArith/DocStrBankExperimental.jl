```
struct LikelihoodRatioTest <: GoodnessOfFit end
const LRT = LikelihoodRatioTest
```

Type indicates conducting ANOVA by likelihood-ratio test. It can be the first argument or keyword argument `test`.
