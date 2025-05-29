`GATContext`

A context consisting of two parts: a GAT and a TypeCtx

Certain types (like AlgTerm) can only be parsed in a GATContext, because they require access to the method resolving in the GAT.
