```
fit!(bls::BestLearner, instances::DataFrame, labels::Vector)
```

Training phase:

  * obtain learners as is if grid option is not present
  * generate learners if grid option is present
  * foreach prototype learner, generate learners with specific options found in grid
  * generate partitions
  * train each learner on each partition and obtain validation output
