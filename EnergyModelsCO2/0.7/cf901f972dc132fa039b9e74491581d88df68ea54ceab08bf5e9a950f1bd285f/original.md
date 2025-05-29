```
NetworkNodeWithRetrofit <:NetworkNode
```

Abstract supertype for allowing retrofitting CO₂ capture to a node. Its application requires the user to

1. define their own node as subtype of `NetworkNodeWithRetrofit` and
2. include a field `co2_proxy` in said node or alternatively define a method for `co2_proxy` for the node.

The application is best explained by [`RefNetworkNodeRetrofit`](@ref) which illustrates it for a [`RefNetworkNode`](@extref EnergyModelsBase.RefNetworkNode) node.
