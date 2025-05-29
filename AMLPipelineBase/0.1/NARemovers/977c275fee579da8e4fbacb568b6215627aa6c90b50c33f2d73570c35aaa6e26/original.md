```
NARemover(
  Dict(
    :name => "nadetect",
    :acceptance => 0.10 # tolerable NAs percentage
  )
)
```

Removes columns with NAs greater than acceptance rate. This assumes that it processes columns of features.  The output column should not be part of input to avoid it being excluded if it fails the acceptance critera.

Implements `fit!` and `transform!`.
