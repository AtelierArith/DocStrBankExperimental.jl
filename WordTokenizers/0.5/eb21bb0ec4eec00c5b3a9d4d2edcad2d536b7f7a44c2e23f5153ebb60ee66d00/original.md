```
tokenizer(sp::SentencePieceModel,text::AbstractString)
```

It does all the preprocessing step needed and perform `decode_forward` and `decode_backward` ouput tokenize tokens as Array{String,1}
