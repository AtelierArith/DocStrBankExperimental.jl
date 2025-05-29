Wire together two ports in an undirected wiring diagram.

A convenience method that creates and sets junctions as needed. Ports are only allowed to have one junction, so if both ports already have junctions, then the second port is assigned the junction of the first. The handling of the two arguments is otherwise symmetric.

FIXME: When both ports already have junctions, the two junctions should be *merged*. To do this, we must implement `merge_junctions!` and thus also `rem_part!`.
