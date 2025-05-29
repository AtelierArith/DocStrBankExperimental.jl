```
Tokenizer{E, D, C}
```

Lazy iterator of tokens of type `E` over data of type `D`. Tokenizers are usually created with the [`tokenize`](@ref) function, and their iterator behaviour are defined by [`make_tokenizer`](@ref).

`Tokenizer` works on any buffer-like object that defines `pointer` and `sizeof`. When iterated, it will return a `Tuple{Integer, Integer, E}`:

  * The first value in the tuple is the 1-based starting index of the token in the buffer
  * The second is the length of the token in bytes
  * The third is the token.

Un-tokenizable data will be emitted as the "error token" which must also be of type `E`.

The `Int` parameter `C` allows multiple tokenizers to be created with the otherwise same type parameters.

See also: [`make_tokenizer`](@ref)
