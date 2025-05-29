```
PassRule()
```

Pass-through rule. Passes relevance through to the lower layer.

Supports layers with constant input and output shapes, e.g. reshaping layers.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = R_j^{k+1}
$$
