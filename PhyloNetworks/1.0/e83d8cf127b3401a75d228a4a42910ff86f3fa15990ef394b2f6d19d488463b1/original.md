```
readnewick(file name)
readnewick(parenthetical description)
readnewick(IO)
```

Read tree or network topology from parenthetical format (extended Newick). If the root node has a single child: ignore (i.e. delete from the topology) the root node and its child edge.

Input: text file or parenthetical format directly. The file name may not start with a left parenthesis, otherwise the file name itself would be interpreted as the parenthetical description. Nexus-style comments (`[&...]`) are ignored, and may be placed after (or instead) of a node name, and before/after an edge length.

A root edge, not enclosed within a pair a parentheses, is ignored. If the root node has a single edge, this one edge is removed.
