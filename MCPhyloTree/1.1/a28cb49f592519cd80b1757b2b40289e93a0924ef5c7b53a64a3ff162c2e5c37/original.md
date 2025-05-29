```
ParseNewick(s::String)::Union{GeneralNode, Array{GeneralNode, 1}}
```

This function takes a string - either a filename or a newick string - and reads the file / string to return an array of trees (represented as Node objects). The file should solely  consist of newick tree representations, separated by line. The function checks for proper  newick formatting, and will return an error if the string / file is incorrectly formatted.

Newick string input: Returns the root of the tree represented by the newick string. Filename input: Returns an Array of Nodes; each Node is the root of the tree represented by a newick string in the file.

  * `s` : newick string or name of file containing newick strings to parse.
