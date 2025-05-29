```
transpose(f₁::FusionTree{I}, f₂::FusionTree{I},
        p1::NTuple{N₁, Int}, p2::NTuple{N₂, Int}) where {I, N₁, N₂}
-> <:AbstractDict{Tuple{FusionTree{I, N₁}, FusionTree{I, N₂}}, <:Number}
```

Input is a double fusion tree that describes the fusion of a set of incoming uncoupled sectors to a set of outgoing uncoupled sectors, represented using the individual trees of outgoing (`t1`) and incoming sectors (`t2`) respectively (with identical coupled sector `t1.coupled == t2.coupled`). Computes new trees and corresponding coefficients obtained from repartitioning and permuting the tree such that sectors `p1` become outgoing and sectors `p2` become incoming.
