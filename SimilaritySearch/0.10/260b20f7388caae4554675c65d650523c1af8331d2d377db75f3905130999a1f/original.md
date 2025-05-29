```
search(bs::BeamSearch, index::SearchGraph, q, res, hints, pools; bsize=bs.bsize, Δ=bs.Δ, maxvisits=bs.maxvisits)
```

Tries to reach the set of nearest neighbors specified in `res` for `q`.

  * `bs`: the parameters of `BeamSearch`
  * `index`: the local search index
  * `q`: the query
  * `res`: The result object, it stores the results and also specifies the kind of query
  * `hints`: Starting points for searching, randomly selected when it is an empty collection
  * `pools`: A SearchGraphPools object with preallocated pools

Optional arguments (defaults to values in `bs`)

  * `bsize`: Beam size
  * `Δ`: exploration expansion factor
  * `maxvisits`: Maximum number of nodes to visit (distance evaluations)
