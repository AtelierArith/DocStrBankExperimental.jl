```
repartition(f₁::FusionTree{I, N₁}, f₂::FusionTree{I, N₂}, N::Int) where {I, N₁, N₂}
-> <:AbstractDict{Tuple{FusionTree{I, N}, FusionTree{I, N₁+N₂-N}}, <:Number}
```

Input is a double fusion tree that describes the fusion of a set of incoming uncoupled sectors to a set of outgoing uncoupled sectors, represented using the individual trees of outgoing (`f₁`) and incoming sectors (`f₂`) respectively (with identical coupled sector `f₁.coupled == f₂.coupled`). Computes new trees and corresponding coefficients obtained from repartitioning the tree by bending incoming to outgoing sectors (or vice versa) in order to have `N` outgoing sectors.
