```
recall_score(gold, predicted; weight=:macro)::Float64
```

It computes the recall between the gold dataset and the list of predictions `predict`

It applies the desired weighting scheme for binary and multiclass problems

  * `:macro` performs a uniform weigth to each class
  * `:weigthed` the weight of each class is proportional to its population in gold
  * `:micro` returns the global recall, without distinguishing among classes
