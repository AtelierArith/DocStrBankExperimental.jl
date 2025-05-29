```
make_tokenizer(
    machine::TokenizerMachine;
    tokens::Tuple{E, AbstractVector{E}}= [ integers ],
    goto=true, version=1
) where E
```

Create code which when evaluated, defines `Base.iterate(::Tokenizer{E, D, $version})`. `tokens` is a tuple of:

  * the error token, which will be emitted for data that cannot be tokenized, and
  * a vector of non-error tokens of length `machine.n_tokens`.

Most users should instead use the more convenient method `make_tokenizer(tokens)`.

# Example usage

```jldoctest
julia> machine = compile([re"a", re"b"]);

julia> make_tokenizer(machine; tokens=(0x00, [0x01, 0x02])) |> eval

julia> iter = tokenize(UInt8, "abxxxba"); typeof(iter)
Tokenizer{UInt8, String, 1}

julia> collect(iter)
5-element Vector{Tuple{Int64, Int32, UInt8}}:
 (1, 1, 0x01)
 (2, 1, 0x02)
 (3, 3, 0x00)
 (6, 1, 0x02)
 (7, 1, 0x01)
```

Any actions inside the input regexes will be ignored.

If `goto` (default), use the faster, but more complex goto code generator.
The `version` number will set the last parameter of the `Tokenizer`, which allows you to create different tokenizers for the same element type.

See also: [`Tokenizer`](@ref), [`tokenize`](@ref), [`compile`](@ref)
