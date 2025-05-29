```
tweet_tokenize(input::AbstractString) => tokens
```

Twitter-aware tokenizer, designed to be flexible and easy to adapt to new domains and tasks.

The basic logic is following:

1. The regular expressions are made for WORD*REGEX (core tokenizer), HANG*REGEX and EMOTICONS_REGEX.

2  Replacing HTML entities, tweet handles, reducing length of repeated characters    and other features, make it suitable for tweets.

3. The String is tokenized and returned.
4. `preserve_case` By default is set to `true`. If it is set to `false`, then the tokenizer will downcase everything except for emoticons.

Example:

```
julia> tweet_tokenize("This is a cooool #dummysmiley: :-) :-P <3 and some arrows < > -> <--")

16-element Array{SubString{String},1}:
 "This"
 "is"
 "a"
 "cooool"
 "#dummysmiley"
 ":"
 ":-)"
 ":-P"
 "<3"
 "and"
 "some"
 "arrows"
 "<"
 ">"
 "->"
 "<--"
```
