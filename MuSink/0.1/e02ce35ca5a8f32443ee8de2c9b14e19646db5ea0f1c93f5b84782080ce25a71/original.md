Core structure for solving UMOT problems. Besides the static properties provided by a `Problem` (tree topology, target and reference measures, cost and penalty functions), a `Workspace` also stores various parameters and auxiliary variables of the optimization problem.

Workspaces are powered by fast implementations of the inner loop of Sinkhorn iterations. These iterations can be performed either in the exponential domain (fast, but breaks down for small regularization parameters `eps`) or the logarithmic domain (slower, but remains stable for small `eps`). The domain can be specified via the keyword argument `logdomain`. The default is `logdomain = true`.

### Sinkhorn steps and update rules

Sinkhorn steps that modify the `Workspace` (or, more precisely, the potentials and auxiliary α-arrays stored in the workspace) can conveniently be performed via the `step!` or `steps!` function. Based on the array type of the workspace, the properties of the cost function (separable or not), and the operating domain (logdomain or expdomain), specialized kernels are used.

Since the order of the updates can influence the stability / convergence of the algorithm, several different update rules (accessible via the keyword argument `stepmode`) are implemented:

  * `stepmode = :legacy`: a backwards pass through the tree (i.e., updating the value of α-arrays from parents to leaves) is followed by a forward pass (i.e., updating the value of α-arrays from leaves to parents) that also updates the potentials. This update rule is proposed by the authors of the original UMOT manuscript and seems to work fine in most configurations. However, in certain situations, the update rule blocks the propagation of information through the tree, such that potential updates within a step remain unaware of one another. A possible consequence is mass oscillation, which prevents convergence. This behavior is explicit in the barycenter problem (e.g., a star-shaped tree topology where the center node has fixed potentials via `rho = 0`) **IF** the root node is set to the center. If the root node is set to a leaf of the tree, `stepmode = :legacy` should always work.
  * `stepmode = :stable`: a backwards pass through the tree is followed by a mixed forward / backward pass that updates the potentials. This update rule fixes the issues of the `:legacy` method but also requires more calculations per step.
  * `stepmode = :alternate`: only a mixed forward / backward pass that updates the potentials is conducted. This update rule uses as many computations per step as the `:legacy` method (i.e., it is faster than the `:stable` method) but should be protected against harmful information barriers. Still, this method is more aggressive and might thus be more susceptible to instabilities than `:stable`.
  * `stepmode = :symmetric`: a backwards pass is followed by a forward pass. Both of these passes update the values of α only. Afterwards, all potentials are updated simultaneously. **This update rule is severely broken for more than two measures and is subject to change or deprecation**

### Parameters

The UMOT problem relies on several parameters to be chosen by the user, like the parameters `eps` (strength of the entropic regularization), `reach` (the interaction radius), or `rho` (strength of the marginal penalty). The latter can be set per node. It is additionally possible to specify the weight of individual edges of the tree, which corresponds to a scaling of the cost function along that edge.
