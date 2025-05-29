```
penn_tokenize(input::AbstractString)
```

"... to produce Penn Treebank tokenization on arbitrary raw text. Yeah, sure" quote Robert MacIntyre

Tokenization does a number of things like seperate out contractions: "shouldn't" becomes ["should", "n't"] Most other punctuation becomes &'s. Exception is periods which are not touched. The input should be a single sentence; but it will likely be relatively fine if it isn't. Depends exactly what you want it for.

This is a direct (automatic) translation of the original sed script.

If you want to mess with exactly what it does it is actually really easy. copy the penn.sed file from this repo, modify it to your hearts content. There are some lines you can uncomment out. You can generate a new tokenizer using:

```
@generated function custom_tokenizer(input::AbstractString)
    generate_tokenizer_from_sed(joinpath(@__DIR__, "custom.sed"))
end
```
