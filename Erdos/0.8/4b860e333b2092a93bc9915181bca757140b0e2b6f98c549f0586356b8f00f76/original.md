```
graph(s::Symbol, G = Graph)
```

Creates a notorious graph `s` of type `G`. Admissible values for `s` are:

| `s`                   | graph type                                                                                             |
|:--------------------- |:------------------------------------------------------------------------------------------------------ |
| :bull                 | A [bull graph](https://en.wikipedia.org/wiki/Bull_graph).                                              |
| :chvatal              | A [Chvátal graph](https://en.wikipedia.org/wiki/Chvátal_graph).                                        |
| :cubical              | A [Platonic cubical graph](https://en.wikipedia.org/wiki/Platonic_graph).                              |
| :desargues            | A [Desarguesgraph](https://en.wikipedia.org/wiki/Desargues_graph).                                     |
| :diamond              | A [diamond graph](http://en.wikipedia.org/wiki/Diamond_graph).                                         |
| :dodecahedral         | A [Platonic dodecahedral  graph](https://en.wikipedia.org/wiki/Platonic_graph).                        |
| :frucht               | A [Frucht graph](https://en.wikipedia.org/wiki/Frucht_graph).                                          |
| :heawood              | A [Heawood graph](https://en.wikipedia.org/wiki/Heawood_graph).                                        |
| :house                | A graph mimicing the classic outline of a house.                                                       |
| :housex               | A house graph, with two edges crossing the bottom square.                                              |
| :icosahedral          | A [Platonic icosahedral   graph](https://en.wikipedia.org/wiki/Platonic_graph).                        |
| :krackhardtkite       | A [Krackhardt-Kite social network  graph](http://mathworld.wolfram.com/KrackhardtKite.html).           |
| :moebiuskantor        | A [Möbius-Kantor graph](http://en.wikipedia.org/wiki/Möbius–Kantor_graph).                             |
| :octahedral           | A [Platonic octahedral graph](https://en.wikipedia.org/wiki/Platonic_graph).                           |
| :pappus               | A [Pappus graph](http://en.wikipedia.org/wiki/Pappus_graph).                                           |
| :petersen             | A [Petersen graph](http://en.wikipedia.org/wiki/Petersen_graph).                                       |
| :sedgewickmaze        | A simple maze graph used in Sedgewick's *Algorithms in C++: Graph  Algorithms (3rd ed.)*               |
| :tetrahedral          | A [Platonic tetrahedral  graph](https://en.wikipedia.org/wiki/Platonic_graph).                         |
| :truncatedcube        | A skeleton of the [truncated cube graph](https://en.wikipedia.org/wiki/Truncated_cube).                |
| :truncatedtetrahedron | A skeleton of the [truncated tetrahedron  graph](https://en.wikipedia.org/wiki/Truncated_tetrahedron). |
| :tutte                | A [Tutte graph](https://en.wikipedia.org/wiki/Tutte_graph).                                            |

A collection of real world graphs is available through the [`readgraph`](@ref) function.
