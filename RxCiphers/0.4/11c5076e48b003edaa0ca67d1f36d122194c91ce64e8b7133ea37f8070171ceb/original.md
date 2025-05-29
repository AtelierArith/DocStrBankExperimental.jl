```
checktokenised(txt::Txt) -> Vector{Int}
```

If `txt` is not tokenised (`txt.is_tokenised == false`), throws a `TokeniseError`. Otherwise, it returns the token vector `txt.tokenised`.
