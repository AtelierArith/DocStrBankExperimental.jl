`get_scc(fst::WFST, i = get_initial(fst;single=true); filter=arc->true)`

Calculates the strongly connected components of 'fst' using Tarjan's algorithm. Returns a tuple `(scc,c,v)`:

  * `scc` are the strongly connected components of `fst`
  * `c` is a boolean array containing the accessibility form the `i`
  * `v` are the visited states of the `fst`

The function `filter` can be used to consider only arcs with specific properties.
