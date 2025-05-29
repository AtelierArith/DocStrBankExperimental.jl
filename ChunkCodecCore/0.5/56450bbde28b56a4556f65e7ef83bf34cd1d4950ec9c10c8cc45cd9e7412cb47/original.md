```
struct DecodedSizeError <: Exception
DecodedSizeError(max_size, decoded_size)
```

Unable to decode the data because the decoded size is larger than `max_size` or smaller than expected. If the decoded size is unknown `decoded_size` is `nothing`.
