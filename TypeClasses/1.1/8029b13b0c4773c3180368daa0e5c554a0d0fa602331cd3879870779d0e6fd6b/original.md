```
orelse(d1::Dict, d2::Dict) -> Dict
```

Following the orelse semantics on Option values, the first value is retained, and the second is dropped. Hence this is the flipped version of `Base.merge`.
