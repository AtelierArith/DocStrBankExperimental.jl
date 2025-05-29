```
auc(scores, events, increasing = true)
```

compute the Area Under the receiver operator Curve (AUC), given some output `scores` array and some ground truth (`events`). By default, it is assumed, that the `scores` are ordered increasingly (`increasing = true`), i.e. high scores represent events. AUC is computed according to Fawcett, T. (2006). An introduction to ROC analysis. Pattern Recognition Letters, 27(8), 861–874. http://doi.org/10.1016/j.patrec.2005.10.010

# Examples

```
julia> scores = rand(10, 2)
julia> events = rand(0:1, 10, 2)
julia> auc(scores, events)
julia> auc(scores, boolevents(events))
```
