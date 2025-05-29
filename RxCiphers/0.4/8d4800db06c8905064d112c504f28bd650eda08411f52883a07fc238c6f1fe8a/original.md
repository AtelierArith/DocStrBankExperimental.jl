```
untokenise(txt::Txt, W::DLMSpace; kwargs) -> String
```

Returns the concatenation of the substrings for tokens in `txt.tokenised`.

# Keyword Arguments

  * `restore_frozen = true` controls whether frozen substrings are reinserted
  * `restore_case = true` controls whether the original cases are reapplied
