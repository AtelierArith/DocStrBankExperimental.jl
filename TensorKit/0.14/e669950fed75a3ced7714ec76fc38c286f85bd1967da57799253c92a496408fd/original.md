```
braid(f₁::FusionTree{I}, f₂::FusionTree{I},
        levels1::IndexTuple, levels2::IndexTuple,
        p1::IndexTuple{N₁}, p2::IndexTuple{N₂}) where {I<:Sector, N₁, N₂}
-> <:AbstractDict{Tuple{FusionTree{I, N₁}, FusionTree{I, N₂}}, <:Number}
```

Input is a fusion-splitting tree pair that describes the fusion of a set of incoming uncoupled sectors to a set of outgoing uncoupled sectors, represented using the splitting tree `f₁` and fusion tree `f₂`, such that the incoming sectors `f₂.uncoupled` are fused to `f₁.coupled == f₂.coupled` and then to the outgoing sectors `f₁.uncoupled`. Compute new trees and corresponding coefficients obtained from repartitioning and braiding the tree such that sectors `p1` become outgoing and sectors `p2` become incoming. The uncoupled indices in splitting tree `f₁` and fusion tree `f₂` have levels (or depths) `levels1` and `levels2` respectively, which determines how indices braid. In particular, if `i` and `j` cross, $τ_{i,j}$ is applied if `levels[i] < levels[j]` and $τ_{j,i}^{-1}$ if `levels[i] > levels[j]`. This does not allow to encode the most general braid, but a general braid can be obtained by combining such operations.
