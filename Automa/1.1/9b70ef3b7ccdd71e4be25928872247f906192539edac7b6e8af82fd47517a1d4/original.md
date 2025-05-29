```
compile(tokens::Vector{RE}; unambiguous=false)::TokenizerMachine
```

Compile the regex `tokens` to a tokenizer machine. The machine can be passed to `make_tokenizer`.

The keyword `unambiguous` decides which of multiple matching tokens is emitted: If `false` (default), the longest token is emitted. If multiple tokens have the same length, the one with the highest index is returned. If `true`, `make_tokenizer` will error if any possible input text can be broken ambiguously down into tokens.

See also: [`Tokenizer`](@ref), [`make_tokenizer`](@ref), [`tokenize`](@ref)
