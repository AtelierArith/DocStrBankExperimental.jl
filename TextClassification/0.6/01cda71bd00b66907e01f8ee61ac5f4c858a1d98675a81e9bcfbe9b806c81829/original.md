```
f1_score(gold, predicted; weight=:macro)::Float64
```

It computes the F1 score between the gold dataset and the list of predictions `predicted`

It applies the desired weighting scheme for binary and multiclass problems

  * `:macro` performs a uniform weigth to each class
  * `:weigthed` the weight of each class is proportional to its population in gold
  * `:micro` returns the global F1, without distinguishing among classes
