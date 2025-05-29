```
search_senses(dict, keyword)
```

Search for the given `keyword` in the dictionary among the meanings/senses (the `keyword` must appear exactly in one or more of the definition senses; this behavior may change in future releases).

## Examples

```julia-repl
julia> search_senses(dict, "fishnet") .|> println;
漁網 (渔网): [yu2 wang3]
        fishing net
        fishnet
扳罾: [ban1 zeng1]
        to lift the fishnet
網襪 (网袜): [wang3 wa4]
        fishnet stockings
```
