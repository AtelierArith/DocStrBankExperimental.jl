## `biconnected_components`

This function requires a symmetric matrix as input. Depending on the user input this function returns either the biconnected component number associated with each edge  or articlation points or both.

## Inputs

  * `A`: the adjacency matrix
  * Optional Keyword inputs

      * `art=true`: returns the articulation points of the graph.
      * `components=true`:returns the biconnected component labels associated with each

    edge.

## Returns

  * Returns a `Biconnected_components_output` type which includes

`map` : biconnected component labels associated with each edge,  `articulation_points`: boolean array that signifies whether a vertex is an articulation point and `number`: Number of biconnected components in the graph.

## Example

A = load*matrix*network("biconnected*example") B = MatrixNetwork(A) bcc = biconnected*components(B) map = bcc.map articulation*vector = bcc.articulation*points number*of*components = bcc.number
