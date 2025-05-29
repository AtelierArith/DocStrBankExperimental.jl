The `FlowMeta` structure contains the meta data of the `Flow` factor node. More specifically, it contains the model of the `Flow` factor node. The `FlowMeta` structure can be constructed as `FlowMeta(model)`. Make sure that the flow model has been compiled.

The `FlowMeta` structure is required for the `Flow` factor node and can be included with the Flow node as: `y ~ Flow(x) where { meta = FlowMeta(...) }`
