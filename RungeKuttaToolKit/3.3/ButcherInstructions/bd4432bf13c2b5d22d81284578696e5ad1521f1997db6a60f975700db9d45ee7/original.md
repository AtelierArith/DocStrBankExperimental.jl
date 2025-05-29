```
all_rooted_trees(
    n::Integer;
    tree_ordering::Symbol=:reverse_lexicographic,
) -> Vector{LevelSequence}
```

Compute and return a list of all rooted trees with **up to** $n$ vertices. Several algorithms that generate rooted trees in different orderings are available:

  * `:reverse_lexicographic` (default) is the asymptotically optimal algorithm   [devised by Terry Beyer and Sandra Mitchell Hedetniemi](https://epubs.siam.org/doi/pdf/10.1137/0209055) that generates rooted   trees in constant time per tree. It generates rooted trees in reverse   lexicographic order of their canonical level sequence representation.   This is the fastest known algorithm, but unlike the others, it produces   the tall tree first and the bushy tree last.
  * `:lexicographic` generates rooted trees in lexicographic order of their   canonical level sequence representation. It simply runs the   `:reverse_lexicographic` algorithm and reverses its output.   This algorithm produces the bushy tree first and the tall tree last.
  * `:attach` generates rooted trees of order $n$ by attaching a leaf to each   vertex of each rooted tree of order $n-1$, starting from the root and   proceeding depth-first. This is the ordering produced by paper-and-pencil   application of the product rule to the set of elementary differentials.   This is the slowest algorithm, but it is arguably the most intuitive.   It produces the bushy tree first and the tall tree last.
  * `:butcher` is [Algorithm 3](https://link.springer.com/content/pdf/10.1007/978-3-030-70956-3_2)   from [John Butcher's monograph on B-Series](https://link.springer.com/content/pdf/10.1007/978-3-030-70956-3.pdf),   which generates rooted trees in a canonical ordering often used in the   literature on Runge–Kutta methods. It produces the bushy tree first and   the tall tree last.
