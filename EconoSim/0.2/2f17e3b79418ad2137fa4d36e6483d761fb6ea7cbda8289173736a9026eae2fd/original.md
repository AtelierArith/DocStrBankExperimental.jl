```
pay!(buyer::Balance,
    seller::Balance,
    price::Price,
    timestamp::Integer;
    comment::String = "")
```

# Returns

A boolean indicating whether the price was paid in full.
