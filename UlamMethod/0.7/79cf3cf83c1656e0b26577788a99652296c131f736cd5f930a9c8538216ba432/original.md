```
struct UlamResult{Dim, M, CRS}
```

A container for the result of the main Ulam's method calculation. 

This consists of three main components, the transition probability matrix, the associated  bins and the bins that were disconnected.

The transition probability matrix is of the form

| `P_O2O` | `P_O2ω` | 

| `P_ω2O` |  `0`  |

Where `O` represents the "open" (interior) region and `ω` reprsents the "nirvana" (exterior) region. The union of `O` and `ω` form a closed region.

### Fields

  * `P_O2O`: As in diagram.
  * `P_O2ω`: As in diagram.
  * `P_ω2O`: As in diagram.
  * `binner`: The [`BinningAlgorithm`](@ref) used to bin the data.
  * `bins_dis`: The bins that contained data but were removed when the largest strongly connected component was taken.

### Methods

```
P_closed(UlamResult)
```

Access the full matrix.

```
P_open(UlamResult)
```

Access `P_O2O`.

```
bins(UlamResult)
```

Access `bins`.

```
bins_dis(UlamResult)
```

Access `bins_dis`.

```
membership(data_or_traj, ulam_result)
```

Compute the membership of `data_or_traj` for the binned domain. See the [`membership`](@ref) function for more information.

```
counts(data_or_traj, ulam_result)
```

Compute the bin counts of `data_or_traj` for the binned domain. See the [`counts`](@ref) function for more information.
