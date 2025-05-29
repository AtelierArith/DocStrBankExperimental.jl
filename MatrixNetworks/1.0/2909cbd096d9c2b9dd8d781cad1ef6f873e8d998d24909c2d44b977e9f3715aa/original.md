# 'generalized*preferential*attachment_graph'

Generate an instance of a generalized preferential attachment graph which follows the Avin,Lotker,Nahum,Peleg description. This is an undirected graph that is generated as follows:

  * Start with a k0-node clique
  * Add n - k0 vertices where at each time step one of three events occurs: A new

node is added with probability p, a new edge between two existing nodes is added with probability r, two new nodes with an edge between them is added with probability 1 - p - r

## Functions

The following functions are synonyms

  * 'generalized*preferential*attachment_graph'
  * 'gpa_graph'

and

  * 'generalized*preferential*attachment_edges!'
  * 'gpa_edges!'

The computational functions are

  * 'gpa_graph(n,p,r,k0)' Generate a GPA graph with a k0 clique and n total nodes.   This returns a MatrixNetwork type
  * 'gpa_graph(n,p,r,k0,Val{true})' Generate a GPA graph with a k0 clique and   n total nodes, allowing self-loops. This returns a MatrixNetwork type

The edge functions are

  * 'gpa_edges!(n,p,r,edges,n0)' Add new edges to an existing set, by taking   n0 time steps. Edges are added in one of three ways: From a new node to   an existing node with probability p, between two existing nodes with   probability r, between two new nodes with probability 1-p-r
  * 'gpa_edges!(n,p,r,edges,n0,Val{true})' Add new edges to an existing set, by   taking n0 time steps. Edges are added in one of three ways: From a new node   to an existing node with probability p, between two existing nodes with   probability r (allowing self-loops), between two new nodes with probability   1-p-r

## Input

  * 'n': the number of nodes in the final graph.
  * 'p': The probability of a node event, p must be a constant.
  * 'r': The probability of an edge event, r must be a constant. p+r <=1
  * 'k0': the number of nodes in the starting clique.
  * 'Val{true}': Include this parameter if self-loops are allowed. Default is false
  * 'edges': A list of edges to be manipulated in the process of generating         new edges.

## Output

  * A matrix network type for the generalized preferential attachment graph.
  * 'edges': An updated list of edges.

Example: generalized*preferential*attachment_graph(100,1/3,1/2,2)
