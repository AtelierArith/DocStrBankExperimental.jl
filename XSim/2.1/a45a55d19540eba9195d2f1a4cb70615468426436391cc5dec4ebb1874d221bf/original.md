### Test

```jldoctest
    handle_h2(missing, 1)    # [0.5]
    handle_h2(missing, 2)    # [0.5, 0.5]
    handle_h2(0.3, 1)        # [0.3]
    handle_h2([0.3], 1)      # [0.3]
    handle_h2([0.3, 0.2], 1) # [0.3]
    handle_h2(0.3, 2)        # [0.3, 0.3]
    handle_h2([0.3], 2)      # [0.3, 0.3]
    handle_h2([0.3, 0.2], 2) # [0.3, 0.2]
```
