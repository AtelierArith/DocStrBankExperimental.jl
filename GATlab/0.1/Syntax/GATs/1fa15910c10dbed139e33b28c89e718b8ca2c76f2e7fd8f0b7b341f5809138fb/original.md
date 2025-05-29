`GAT`

A generalized algebraic theory. Essentially, just consists of a name and a list of `GATSegment`s, but there is also some caching to make access faster. Specifically, there is a dictionary to map ScopeTag to position in the list of segments, and there are lists of all of the identifiers for term constructors, type constructors, and axioms so that they can be iterated through faster.

GATs allow overloading but not shadowing.
