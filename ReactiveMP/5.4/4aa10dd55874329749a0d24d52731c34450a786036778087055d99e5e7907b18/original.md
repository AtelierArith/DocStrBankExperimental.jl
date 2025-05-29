The BIFMHelper node is a node required to perform efficient message passing inconjuction with the BIFM node. It is required to switch from the backward pass with messages to the forward pass with marginals.

```julia
out ~ BIFMHelper(in)
```

Interfaces:

1. out - output of the BIFMHelper node, should be connected to the state space model.
2. in - input of the BIFMHelper node, should be connected to the prior for the latent state.

*Note: When performing inference, first subscribe to the marginals (in the order: z, out, in) and then to the free energy score function.*
