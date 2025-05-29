```
StandardScaling <: AbstractScaling
```

Transforms the data according to

```
x -> (x - μ) / σ
```

where μ and σ are the mean and standard deviation of the training data.

!!! note
    `fit!(scaling, data)` needs to be called before the transform can be `apply`ed. By default *all the data* is considered when `fit!`ing the mean and standard deviation.

