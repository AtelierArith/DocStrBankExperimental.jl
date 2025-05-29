```
ber()
```

Computes the Bayes Error Rate.  This computes the expected error rate given a set of supervised trials, the log-likelihood-ratio scores `tar` and `non`, and a threshold based on a given a cost function specified by its prior log-odds (see `plo()`).

If the scores `tar` and `non` are well-calibrated log-likelihood-ratios, the optimum decision threshold that minimizes the decision cost function `dcf` is surprisingly simple,

```
θ = -plo(dcf).
```

This function computes the actual cost for such decisions, given the test scores.

Arguments:

  * `tar::Vector`, `non::Vector`, `plo`: target and non-target llr

scores, and prior log odds.  Here, `plo` may be a vector, resulting in multiple Bayes error rates.

  * `r::Roc`, `plo`: a `Roc` structure computed with `roc(;collapse=false)`.

It is mandatory that the Roc object is not collapsed, because the actual cost may occur for a threshold between two "corner" points of the ROC curve.  A `Roc` structure is useful for computing the minimum Bayes Error Rate for multiple cost functions–-in this case the `Roc` may be `collapse`d.

  * `; thres`: an optional threshold, overriding the theoretical

optimum described above.  This can be used if the scores are not correctly calibrated.
