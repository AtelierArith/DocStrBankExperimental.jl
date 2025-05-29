```
description(daf::DafReader[; deep::Bool = false, cache::Bool = false])::AbstractString
```

Return a (multi-line) description of the contents of `daf`. This tries to hit a sweet spot between usefulness and terseness. If `cache`, also describes the content of the cache. If `deep`, also describes any data set nested inside this one (if any).
