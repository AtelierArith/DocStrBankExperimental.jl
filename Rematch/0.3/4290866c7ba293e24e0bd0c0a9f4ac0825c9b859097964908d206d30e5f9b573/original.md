```
@match value begin
    pattern1 => result1
    pattern2 => result2
    ...
end
```

Return `result` for the first matching `pattern`. If there are no matches, throw `MatchFailure`.
