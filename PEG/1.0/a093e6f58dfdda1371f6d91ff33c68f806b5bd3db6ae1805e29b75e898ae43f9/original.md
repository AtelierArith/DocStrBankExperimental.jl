```
parse_next(rule, input; whole=false)
```

Parse a prefix of the `input` string as one instance of the given `rule`. This differs from just calling the `rule` itself on the `input` in a few important ways:

  * When parsing succeeds, `parse_next` returns only the parsed value, while `rule` returns a Tuple of the parsed value and the remaining unparsed input.
  * When parsing fails, `parse_next` throws an exception, with information on what failed to match starting at the latest point in the string that any parsing expression matched up to. `rule` just returns `nothing`.
  * When `whole=true`, parsing only succeeds if the whole input is consumed, i.e. the second value in the tuple that `rule` returns is `""`.
