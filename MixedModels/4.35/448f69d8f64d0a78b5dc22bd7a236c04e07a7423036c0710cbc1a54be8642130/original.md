```
pvalue(lrt::LikelihoodRatioTest)
```

Extract the p-value associated with a likelihood ratio test.

For `LikelihoodRatioTest`s containing more than one model comparison, i.e. more than two models, this throws an error because it is unclear which p-value is desired.

To get p-values for multiple tests, use `lrt.pvalues`.
