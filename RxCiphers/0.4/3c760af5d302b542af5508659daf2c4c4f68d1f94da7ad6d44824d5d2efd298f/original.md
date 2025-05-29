```
tokenise(txt::Txt, W::DLMSpace) -> Vector{Int}, Dict{Int, String}
```

Returns the token vector of `txt`, where raw substrings have been encoded as tokens (integers), according to the mapping of the characterspace `W` and returns the `frozen` dictionary, which stores the location of substrings that do not get tokenised
