```
XPRS_PREDICTEDATTLEVEL
```

A measure between 0 and 1 to predict how numerically unstable the current MIP solve can be expected to be. (double)

After the root LP solve, a machine learning model is used to predict the actual ATTENTIONLEVEL which will only be computed if MIPKAPPAFREQ is set to a nonzero value. If the predicted attention level exceeds a value of 0.1, a message will be printed to the log.
