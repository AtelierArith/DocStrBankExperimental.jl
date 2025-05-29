```
mcc(tn::T, fp::T, fn::T, tp::T) where {T<:Integer}
```

Matthews correlation coefficient, a special case of the phi coeficient Performance metric used for overcoming the class imbalance issues

# Arguments

  * `tn::Integer` True negatives
  * `fp::Integer` False postives
  * `fn::Integer` False negatives
  * `tp::Integer` True positives

# Reference

1.Chicco, D., Jurman, G. The advantages of the Matthews correlation coefficient (MCC) over F1 score and accuracy in binary classification evaluation. BMC Genomics 21, 6 (2020).
