```
soft_assignment(conf_model::ConformalProbabilisticSet; temp::Real=0.1)
```

Computes soft assignment scores for each label and sample. That is, the probability of label `k` being included in the confidence set. This implementation follows Stutz et al. (2022): https://openreview.net/pdf?id=t8O-4LKFVx. Contrary to the paper, we use non-conformity scores instead of conformity scores, hence the sign swap. 
