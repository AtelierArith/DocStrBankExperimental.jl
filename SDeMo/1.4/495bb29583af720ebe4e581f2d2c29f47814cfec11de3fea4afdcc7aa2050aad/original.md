```
train!(sdm::SDM; threshold=true, training=:, optimality=mcc)
```

This is the main training function to train a SDM.

The three keyword arguments are:

  * `training`: defaults to `:`, and is the range (or alternatively the indices) of the data that are used to train the model
  * `threshold`: defaults to `true`, and performs moving threshold by evaluating 200 possible values between the minimum and maximum output of the model, and returning the one that is optimal
  * `optimality`: defaults to `mcc`, and is the function applied to the confusion matrix to evaluate which value of the threshold is the best
  * `absences`: defaults to `false`, and indicates whether the (pseudo) absences are used to train the transformer; when using actual absences, this should be set to `true`

Internally, this function trains the transformer, then projects the data, then trains the classifier. If `threshold` is `true`, the threshold is then optimized.
