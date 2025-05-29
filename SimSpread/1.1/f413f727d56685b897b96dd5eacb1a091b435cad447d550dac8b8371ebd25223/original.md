```
mcc(a::T, b::T, ϵ::AbstractFloat = 0.0001) where {T<:Integer}
```

Matthews correlation coefficient using calculus approximation for when FN+TN, FP+TN, TP+FN or TP+FP equals zero.

# Arguments

  * `a::Integer` = Value of position `a` in confusion matrix
  * `b::Integer` = Value of position `b` in confusion matrix
  * `ϵ::AbstractFloat` = Approximation coefficient (default = floatmin(Float64))

# Extended help

The confusion matrix in a binary prediction is comprised of 4 distinct positions:

```
                    | Predicted positive     Predicted negative
    ----------------+--------------------------------------------
    Actual positive |  True positives (TP)   False negatives (FN)
    Actual negative | False positives (FP)    True negatives (TN)
```

In the case a row or column of the confusion matrix equals zero, MCC is undefined. Therefore, to correctly use MCC with this approximation, arguments `a` and `b` are defined as follows:

  * If "Predictive positive" column is zero, `a` is TN and `b` is FN
  * If "Predictive negative" column is zero, `a` is TP and `b` is FP
  * If "Actual positive" row is zero, `a` is TN and `b` is FP
  * If "Actual negative" row is zero, `a` is TP and `b` is FN

# Reference

1.Chicco, D., Jurman, G. The advantages of the Matthews correlation coefficient (MCC) over F1 score and accuracy in binary classification evaluation. BMC Genomics 21, 6 (2020).
