```
struct OctreeConfig
```

Stores config parameters for building octree

|             Parameter |              type |                                                                                         usage |                        Default value |
| ---------------------:| -----------------:| ---------------------------------------------------------------------------------------------:| ------------------------------------:|
|             `NumData` |       `<:Integer` |                                                                   Total number of data points |                                    - |
|          `MaxTopnode` |       `<:Integer` |                                                                    Maximum number of topnodes |                                10000 |
|         `MaxTreenode` |       `<:Integer` |                                                                   Maximum number of treenodes |                               100000 |
|       `TopnodeFactor` |           `Int64` | Controls how many blocks that Peano-Hilbert curve is cut into while dividing computing domain |                                   20 |
|        `ExtentMargin` | `<:AbstractFloat` |                Enlarge the extent a bit to make sure that all particles are inside the domain |                                1.001 |
|         `PeanoBits2D` |           `Int64` |       Peano bit length used in each axis. the last Peano key would be $2^(2*PeanoBits2D) - 1$ |                                   31 |
|         `PeanoBits3D` |           `Int64` |       Peano bit length used in each axis. the last Peano key would be $2^(3*PeanoBits3D) - 1$ |                                   21 |
|             `epsilon` |         `Float64` |                                                Controls the precision of tree leaf seperation |                               1.0e-4 |
| `ToptreeAllocSection` |       `<:Integer` |                           If out of Toptree nodes, append corresponding number of empty nodes | $NumDataBase$ * $ToptreeAllocFactor$ |
|    `TreeAllocSection` |       `<:Integer` |                            If out of Octree nodes, append corresponding number of empty nodes |    $NumDataBase$ * $TreeAllocFactor$ |

Notes:

1. `NumDataBase` is the decimal base of total number of data points.
2. Use `ToptreeAllocFactor` and `TreeAllocFactor` to control `ToptreeAllocSection` and `TreeAllocSection` respectively.
