```
Mecab
```

A mutable struct representing a MeCab tagger. It is created by calling the `Mecab()` constructor.

# Examples

```julia
tagger = Mecab()
results = parse(mecab, "すももももももももものうち")
```
