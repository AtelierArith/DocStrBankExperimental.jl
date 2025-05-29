```
VoteEnsemble(
   Dict( 
      # Output to train against
      # (:class).
      :output => :class,
      # Learners in voting committee.
      :learners => [PrunedTree(), Adaboost(), RandomForest()]
   )
)
```

Set of machine learners employing majority vote to decide prediction.

Implements: `fit!`, `transform!`
