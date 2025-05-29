```
nltk_word_tokenize(input)
```

NLTK's word tokenizer. It is an extension on the Punctuation Preserving Penn Treebank tokenizer, mostly to better handle unicode.

Punctuation is still preserved as its own token. This includes periods which will be stripped from words.

The tokenizer still seperates out contractions: "shouldn't" becomes ["should", "n't"]

The input should be a single sentence; but again it will likely be relatively fine if it isn't. Depends exactly what you want it for.

This matches to the most commonly used `nltk.word_tokenize`, minus the sentence tokenizing step.
