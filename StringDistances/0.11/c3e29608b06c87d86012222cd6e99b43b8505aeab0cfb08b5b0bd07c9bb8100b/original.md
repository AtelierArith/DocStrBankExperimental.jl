```
JaroWinkler(;p = 0.1, threshold = 0.3, maxlength = 4)
```

Creates the JaroWinkler distance

The JaroWinkler distance is defined as the Jaro distance, which is multiplied by $(1-min(l,  maxlength) * p)$ as long as it is lower than `threshold`, and where `l` denotes the length of the common prefix.
