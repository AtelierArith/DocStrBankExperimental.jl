```
StackEnsemble(
   Dict(    
      # Output to train against
      # (:class).
      :output => :class,
      # Set of learners that produce feature space for stacker.
      :learners => [PrunedTree(), Adaboost(), RandomForest()],
      # Machine learner that trains on set of learners' outputs.
      :stacker => RandomForest(),
      # Proportion of training set left to train stacker itself.
      :stacker_training_proportion => 0.3,
      # Provide original features on top of learner outputs to stacker.
      :keep_original_features => false
   )
)
```

An ensemble where a 'stack' of learners is used for training and prediction.
