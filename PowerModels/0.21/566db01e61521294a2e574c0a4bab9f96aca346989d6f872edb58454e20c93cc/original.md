attempts to deactive components that are not needed in the network by repeated calls to `propagate_topology_status!` and `deactivate_isolated_components!`

warning: this implementation has quadratic complexity, in the worst case
