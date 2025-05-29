CVI_MODULES

# Description

List of implemented CVIs, useful for iteration. Each element is the struct abbreviated name for the CVI, which can be instantiated for iteration with the empty constructor.

For example:

```julia
using ClusterValidityIndices
instantiated_cvis = [local_cvi() for local_cvi in CVI_MODULES]
```
