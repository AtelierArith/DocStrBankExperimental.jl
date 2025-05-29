```
BestLearner(
   Dict(
      # Output to train against
      # (:class).
      :output => :class,
      # Function to return partitions of instance indices.
      :partition_generator => (instances, labels) -> kfold(size(instances, 1), 5),
      # Function that selects the best learner by index.
      # Arg learner_partition_scores is a (learner, partition) score matrix.
      :selection_function => (learner_partition_scores) -> findmax(mean(learner_partition_scores, dims=2))[2],      
      # Score type returned by score() using respective output.
      :score_type => Real,
      # Candidate learners.
      :learners => [PrunedTree(), Adaboost(), RandomForest()],
      # Options grid for learners, to search through by BestLearner.
      # Format is [learner_1_options, learner_2_options, ...]
      # where learner_options is same as a learner's options but
      # with a list of values instead of scalar.
      :learner_options_grid => nothing
   )
)
```

Selects best learner from the set by performing a  grid search on learners if grid option is indicated.
