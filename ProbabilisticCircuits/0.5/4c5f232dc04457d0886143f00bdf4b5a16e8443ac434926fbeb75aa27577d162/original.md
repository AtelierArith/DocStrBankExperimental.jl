```
hclt(data, num_hidden_cats; num_cats = nothing, input_type = LiteralDist)
```

Learns HiddenChowLiuTree (hclt) circuit structure from data.

  * `data`: Matrix or CuMatrix
  * `num_hidden_cats`: Number of categories in hidden variables
  * `input_type`: Distribution type for the inputs
  * `num_cats`: Number of categories (in case of categorical inputs). Automatically deduced if not given explicilty.
