```
digraph(s::Symbol, G = DiGraph)
```

Creates a notorious digraph `s` of type `G`. Admissible values for `s` are:

| `s`                   | graph type                                                                                              |
|:--------------------- |:------------------------------------------------------------------------------------------------------- |
| :truncatedtetrahedron | A skeleton of the [truncated tetrahedron digraph](https://en.wikipedia.org/wiki/Truncated_tetrahedron). |
