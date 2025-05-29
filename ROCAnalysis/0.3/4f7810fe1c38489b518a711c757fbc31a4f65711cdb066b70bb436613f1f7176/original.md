```
cllr(tar, non)
```

Computes the cost of the log-likelihood-ratio, for log-likelihood-ratio (llr) scores `tar` and `non` (target scores and non-target scores).  Target an non-target llr's are those for which  the numerator `H1` and denominator `H2` hypothesis are actually true in the log-likelihood-ratio 

```
llr(x) = p(x | H1) / p(x | H2)
```

where `x` is the test data for a system trying to disciminate between `H1` and `H2` given `x`.  

The Cllr of a perfect system, assigning a llr of `+Inf` to target scores and `-Inf` to non-target scores is 0; for a system that is indifferent, producing a `llr=0` for every input `x`, the `Cllr = 1`.   Please note that, for badly calibrated systems, `Cllr > 1`.  The units of Cllr are measured in *bits*,  and cllr can be seen as the average amount of information per trial that is *not* extracted from the  data. 

Cllr measures the *calibration* as well as *discrimination* ability of a system.  Discrimination  entails the ability to produces target scores that are, typically, much higher than non-target scores.   Calibration entails that for every individual `x` an optimal Bayes decision can be made if a  cost function is known.  
