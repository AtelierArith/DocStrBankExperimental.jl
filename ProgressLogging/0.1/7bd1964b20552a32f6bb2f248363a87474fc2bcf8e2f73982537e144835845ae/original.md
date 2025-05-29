```
@progress [name="", threshold=0.005] for i = ..., j = ..., ...
@progress [name="", threshold=0.005] x = [... for i = ..., j = ..., ...]
```

Show a progress meter named `name` for the given loop or array comprehension if possible. Update frequency is limited by `threshold` (one update per 0.5% of progress by default).
