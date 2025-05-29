`shortest_distance(fst[, s=get_initial(fst); filter=arc->true, reverse=false)`

Computes the shortest distance between the state `s` to every other state. The shortest distance between `s` and `i` is defined as the sum of the weights of all paths between these states.

Weights are required to be rigth distributive and k-closed.

If `fst` has `N` states a `N`-long vector is returned where the `i`-the element contains the shortest distance between the states `s` and `i`.

If `reversed==true` the shortest distance from the final states is computed. In this case `s` has no effect since a new initial superstate is added to the reversed WFST. Here weights are required to be left distributive and k-closed. 

See Mohri "Semiring framework and algorithms for shortest-distance problems", Journal of Automata, Languages and Combinatorics 7(3): 321-350, 2002.
