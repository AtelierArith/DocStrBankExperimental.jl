```
improved_penn_tokenize(input::AbstractString)
```

The Improved Penn Treebank tokenizer. This is a port of NLTK's modified Penn Tokenizer. It has a bundle of minor changes, that I don't think are actually documented anywhere. But things like `cannot cannot` become `can not can not` where as the original would produce `can not cannot`.

The tokenizer still seperates out contractions: "shouldn't" becomes ["should", "n't"]

The input should be a single sentence; but again it will likely be relatively fine if it isn't. Depends exactly what you want it for.

This matches NLTK's `nltk.tokenize.TreeBankWordTokenizer.tokenize`
