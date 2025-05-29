```
mutable struct ModelParam ⋯ end
```

Contains a model parameter. For a simple parameter it simply stores its value. For a link or an alias, it stores the link information and also caches the current value for speed.
