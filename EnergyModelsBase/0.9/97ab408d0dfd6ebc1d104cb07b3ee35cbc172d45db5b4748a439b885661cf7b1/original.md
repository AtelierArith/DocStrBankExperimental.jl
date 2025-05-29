```
struct Direct <: Link
```

A direct link between two nodes.

# Fields

  * **`id`** is the name/identifier of the link.
  * **`from::Node`** is the node from which there is flow into the link.
  * **`to::Node`** is the node to which there is flow out of the link.
  * **`formulation::Formulation`** is the used formulation of links. If not specified, a `Linear` link is assumed.
