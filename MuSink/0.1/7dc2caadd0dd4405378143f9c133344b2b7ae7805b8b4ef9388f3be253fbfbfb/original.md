Structure that facilitates calculating (parts of) the transport plan between two nodes.

Since the full transport plan is often impractically large, this type provides a lazy interface that operates on the dual potentials.

Some of the operations on `Coupling`s can only be implemented performantly when nodes are adjacent. These operations fail for couplings between non-neighboring nodes.
