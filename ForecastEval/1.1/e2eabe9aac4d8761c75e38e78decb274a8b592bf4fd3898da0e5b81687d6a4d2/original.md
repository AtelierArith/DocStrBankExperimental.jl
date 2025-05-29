```
DMTest(rejH0::Int, pvalue::Float64, bestinput::Int, teststat::Float64, dmmethod::DMMethod)
```

Output type for a Diebold-Mariano test. A description of the fields follows: 

```
rejH0 <- true if the null is rejected, false otherwise
pvalue <- p-value from the test
bestinput <- 1 if forecast 1 is more accurate, and 2 if forecast 2 is more accurate. See ?dm for definition of forecast 1 versus 2.
teststat <- If dmmethod == :hac then is the mean of loss difference scaled by HAC variance
            If dmmethod == :boot then is the mean of loss difference
dmmethod <- Diebold-Mariano method used in the test. See ?DMMethod for more detail.
```
