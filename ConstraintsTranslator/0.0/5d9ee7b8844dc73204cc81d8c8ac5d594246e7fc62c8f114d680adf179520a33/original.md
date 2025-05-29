```
parse_code(s::String)
```

Parse the code blocks in the input string `s` delimited by triple backticks and an optional language annotation. Returns a dictionary keyed by language. Code blocks from the same language are concatenated.
