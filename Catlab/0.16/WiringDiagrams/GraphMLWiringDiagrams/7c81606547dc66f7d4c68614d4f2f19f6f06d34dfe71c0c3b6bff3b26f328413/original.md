Serialize abstract wiring diagrams as GraphML.

Serialization of box, port, and wire values can be overloaded by data type (see `convert_to_graphml_data` and `convert_from_graphml_data`).

GraphML is the closest thing to a de jure and de facto standard in the space of graph data formats, supported by a variety of graph applications and libraries. We depart mildly from the GraphML spec by allowing JSON data attributes for GraphML nodes, ports, and edges.

References:

  * GraphML Primer: http://graphml.graphdrawing.org/primer/graphml-primer.html
  * GraphML DTD: http://graphml.graphdrawing.org/specification/dtd.html
