A `StringGraph` is a `UndirectedGraph` whose vertices are of type `String`.

When constructed with `StringGraph()` creates an empty `UndirectedGraph{String}`.

When invoked as `StringGraph(file::AbstractString)` opens the named file for parsing as a graph. Each line of the file should contain one or two tokens separated by white space. If the line contains a single token, we add that token as a vertex. If the line contains two (or more) tokens, then the first two tokens are taken as vertex names and (assuming they are different) the corresponding edge is created. Any extra tokens on the line are ignored. Lines that begin with a # are ignored.
