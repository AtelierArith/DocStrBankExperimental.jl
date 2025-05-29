```
Dropout(p) # 0 < p < 1
```

Dropout layer.

When evaluated without gradients, it multiplies inputs by `(1 - p)`. When evaluated with gradients, it randomly zeros `p` proportion of inputs.
