The edge-wise objective function to optimise. These values are natively supported:

  * `Load`: the load of each edge is considered.
  * `KleinrockLoad`: Kleinrock function is applied on the load.
  * `FortzThorupLoad`: Fortz-Thorup linearisation of Kleinrock function is applied on the load.

Kleinrock function is defined as:

$K(x) = \frac{x}{1-x}$
