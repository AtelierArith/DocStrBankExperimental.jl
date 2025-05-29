```
softmax_cross_entropy_with_logits(logits::Union{Array, PyObject}, labels::Union{Array, PyObject})
```

Computes softmax cross entropy between `logits` and `labels`

`logits` is typically the output of a linear layer. For example,

```
logits = [
    0.124575  0.511463   0.945934
    0.538054  0.0749339  0.187802
    0.355604  0.052569   0.177009
    0.896386  0.546113   0.456832
]
labels = [2;1;2;3]
```

!!! info
    The values of `labels` are from  {1,2,...,`num_classes`}. Here `num_classes` is the number of columns in `logits`.


The predicted labels associated with `logits` is 

```
argmax(softmax(logits), dims = 2)
```

Labels can also be one hot vectors 

```
labels = [0 1
          1 0
          0 1
          0 1]
```
