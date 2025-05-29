```
explain([io=stdout], match; context=40)
```

Prints a human-readable explanation of the match and its context in the document in which it was found.

## Example

```jldoctest
julia> document = Document("The crabeating macacue ate a crab.")
Document starting with "The crabeating macacue…". Metadata: NamedTuple()

julia> query = augment(FuzzyQuery("crab-eating macaque"))
Or
├─ FuzzyQuery("crab eating macaque", DamerauLevenshtein{Nothing}(nothing), 2)
├─ FuzzyQuery("crabeating macaque", DamerauLevenshtein{Nothing}(nothing), 2)
├─ FuzzyQuery("crab eatingmacaque", DamerauLevenshtein{Nothing}(nothing), 2)
└─ FuzzyQuery("crabeatingmacaque", DamerauLevenshtein{Nothing}(nothing), 2)

julia> m = match(query, document)
QueryMatch with distance 1 at indices 5:22.

julia> explain(m)
The query "crabeating macaque" matched the text "The crabeating macacue ate a crab  " with distance 1.

julia> explain(m; context=5) # tweak the amount of context printed
The query "crabeating macaque" matched the text "The crabeating macacue ate…" with distance 1.

julia> sprint(explain, m) # to get the explanation as a string
"The query \"crabeating macaque\" matched the text \"The crabeating macacue ate a crab  \" with distance 1.\n"

julia> explain(match(Query("crab"), document)) # exact queries print slightly differently
The query "crab" exactly matched the text "The crabeating macacue ate a crab  ".

julia> explain(match(NamedQuery(Query("crab"), "crab query"), document)) # `NamedQuery`s print the same as their underlying query
The query "crab" exactly matched the text "The crabeating macacue ate a crab  ".

```
