```
pprint([io::IO,] tree; indent=2, multiline=true)
```

Print a constituency parse tree in bracketed format.

# Arguments

  * `io`: `IO` stream to write the tree to
  * `tree`: the tree to search

# Keywords

  * `multiline=true`: whether to include newlines in string representation
  * `indent=2`: how many characters of whitespace to use in indentation (ignored if `multiline` is `false`)

# Returns

  * bracketed `String` representation of the parse tree
