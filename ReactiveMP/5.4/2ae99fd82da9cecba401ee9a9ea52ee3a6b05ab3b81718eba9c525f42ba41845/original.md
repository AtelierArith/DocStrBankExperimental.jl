The FlowModel structure is the most generic type of Flow model, in which the layers are not constrained to be of a specific type. The FlowModel structure contains the input dimensionality and a tuple of layers and can be constructed as `FlowModel( dim, (layer1, layer2, ...) )`.

Note: this model can be specialized by constraining the types of layers. This potentially allows for more efficient specialized methods that can deal with specifics of these layers, such as triangular jacobian matrices.
