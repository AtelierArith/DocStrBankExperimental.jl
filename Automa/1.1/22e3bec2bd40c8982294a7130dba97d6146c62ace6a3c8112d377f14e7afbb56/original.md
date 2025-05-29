```
make_tokenizer(
    tokens::Union{
        AbstractVector{RE},
        Tuple{E, AbstractVector{Pair{E, RE}}}
    };
    goto::Bool=true,
    version::Int=1,
    unambiguous=false
) where E
```

Convenience function for both compiling a `TokenizerMachine`, then running `make_tokenizer` on it. In other words, this function returns code that when run, defines `iterate` for `Tokenizer{$E, D, $version} where D`.

If tokens are a tuple, the first element is the error token, and the next is a vector of `token => regex` pairs. If `tokens` is an `AbstractVector{RE}` `v`, the tokens defaults to `UInt32`, and it behaves as if it was `(UInt32(0), [UInt32(i)=>r for (i,r) in pairs(v)])`, i.e. `UInt32(0)` is the error token.

# Example

```jldoctest
julia> make_tokenizer([re"abc", re"def"]) |> eval

julia> collect(tokenize(UInt32, "abcxyzdef123"))
4-element Vector{Tuple{Int64, Int32, UInt32}}:
 (1, 3, 0x00000001)
 (4, 3, 0x00000000)
 (7, 3, 0x00000002)
 (10, 3, 0x00000000)

julia> make_tokenizer((0, collect(pairs([re"x", re"y"]))); version=5) |> eval

julia> iter = tokenize(Int, "xyaby", 5)
Tokenizer{Int64, String, 5}("xyaby")

julia> collect(iter)
4-element Vector{Tuple{Int64, Int32, Int64}}:
 (1, 1, 1)
 (2, 1, 2)
 (3, 2, 0)
 (5, 1, 2)
```
