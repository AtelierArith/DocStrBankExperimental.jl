Create an encapsulating box for a set of boxes in a wiring diagram.

To a first approximation, the union of input ports of the given boxes will become the inputs ports of the encapsulating box and likewise for the output ports. However, when copies or merges occur, as in a cartesian or cocartesian category, a simplification procedure may reduce the number of ports on the encapsulating box.

Specifically:

1. Each input port of an encapsulated box will have at most one incoming wire

from the encapsulating outer box, and each output port of an encapsulated box will have at most one outgoing wire to the encapsulating outer box.

2. A set of ports connected to the same outside (non-encapsulated) ports will be

simplified into a single port of the encapsulating box.

See also `induced_subdiagram`.
