```
delta([::Type{ElT} = Float64, ]inds)
delta([::Type{ElT} = Float64, ]inds::Index...)
```

Make a uniform diagonal ITensor with all diagonal elements `one(ElT)`. Only a single diagonal element is stored.

This function has an alias `δ`.
