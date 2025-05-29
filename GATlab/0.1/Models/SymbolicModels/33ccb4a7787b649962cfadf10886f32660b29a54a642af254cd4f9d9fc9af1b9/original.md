Functor from GAT expression to GAT instance.

Strictly speaking, we should call these "structure-preserving functors" or, better, "model homomorphisms of GATs". But this is a category theory library, so we'll go with the simpler "functor".

A functor is completely determined by its action on the generators. There are several ways to specify this mapping:

1. Specify a Julia instance type for each GAT type, using the required `types` tuple. For this to work, the generator constructors must be defined for the instance types.
2. Explicitly map each generator term to an instance value, using the `generators` dictionary.
3. For each GAT type (e.g., object and morphism), specify a function mapping generator terms of that type to an instance value, using the `terms` dictionary.

The `terms` dictionary can also be used for special handling of non-generator expressions. One use case for this capability is defining forgetful functors, which map non-generators to generators.

FIXME
