Compose a `CitableTextCorpus` citable at token level. Optional parameters allow you to filter the resulting corpus by a specified token type `filterby`, and a function `normalizer` to apply to tokens to normalize their orthography (e.g., to normalize case or accent).

```julia
tokenizedcorpus(v; filterby, normalizer)

```
