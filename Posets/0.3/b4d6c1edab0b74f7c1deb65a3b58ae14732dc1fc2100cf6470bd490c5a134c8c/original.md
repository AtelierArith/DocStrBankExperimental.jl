A `Poset` is a (strict) partially ordered set on elements `{1,2,...,n}`.

Basic constructors:

  * `Poset(n::Integer = 0)` create a poset with `n` elements (no relations).
  * `Poset(d::DiGraph)` create a poset for a directed acyclic graph.
  * `Poset(p::Poset)` copy constructor.
