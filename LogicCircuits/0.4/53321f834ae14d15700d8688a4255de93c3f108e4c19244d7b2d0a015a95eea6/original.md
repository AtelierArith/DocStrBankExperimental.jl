A bit circuit is a low-level representation of a logical circuit structure.

They are a "flat" representation of a circuit, essentially a bit string, that can be processed by lower level code (e.g., GPU kernels)

The wiring of the circuit is captured by two matrices: nodes and elements.

  * Nodes are either leafs or decision (disjunction) nodes in the circuit.
  * Elements are conjunction nodes in the circuit.
  * In addition, there is a vector of layers, where each layer is a list of node ids. Layer 1 is the leaf/input layer. Layer end is the circuit root.
  * And there is a vector of parents, pointing to element id parents of decision nodes.

Nodes are represented as a 4xN matrix where

  * nodes[1,:] is the first element id belonging to this decision
  * nodes[2,:] is the last element id belonging to this decision
  * nodes[3,:] is the first parent index belonging to this decision
  * nodes[4,:] is the last parent index belonging to this decision

Elements belonging to node `i` are `elements[:, nodes[1,i]:nodes[2,i]]`   Parents belonging to node `i` are `parents[nodes[3,i]:nodes[4,i]]`

Elements are represented by a 3xE matrix, where 

  * elements[1,:] is the decision node id (parents of the element),
  * elements[2,:] is the prime node id (child of the element)
  * elements[3,:] is the sub node id (child of the element)
