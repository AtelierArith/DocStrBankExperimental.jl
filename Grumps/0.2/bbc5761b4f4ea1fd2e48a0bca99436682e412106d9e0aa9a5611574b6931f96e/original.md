```
DataOptions(; 
    micromode   = :Hog
    macromode   = :Ant
    balance     = :micro
    σ2          = 1.0
    id          = :Grumps
)
```

Both this method and the one described below specify how Grumps should store its data and what it should store.  This one is simpler but has less flexibility.  The first three options are best set to their defaults, unless you know what it is you're doing.  The **σ2** option is the variance of ξ, i.e. the error variance in the product level moments.  The **id** option is used to extend Grumps with other data constructions.

```
DataOptions(
    VarξInput   :: VarξInput{T},
    VarξOutput  :: VarξOutput = VarξDefaultOutput,
    micromode   :: Symbol = :Hog,
    macromode   :: Symbol = :Ant,
    balance     :: Symbol = :micro,
    id          :: Symbol = :Grumps   
)
```

Both this method and the one described above specify how Grumps should store its data and what it should store.  This one is both more complex and more flexible.  The **micromode**, **macromode**, and **balance** arguments are best kept at their defaults, unless you know what it is you're doing.  The **id** option is used to extend Grumps with other data constructions.  **VarξInput** is the variance matrix to be used in the penalty term weight matrix construction.  This should be a J by J matrix where J is the number of products across all markets.  Acceptable types for **VarξInput** include UniformScaling{T} (e.g. 1.0 * I ) and AbstractMatrix{T} (sparse matrix is recommended to conserve space, but a dense matrix is allowed).  **VarξOutput** is used to indicate what assumptions on the variance of ξ must be produced in the solution, which can subsequently be used as an input in a second stage if desirable; options are *VarξHomoskedastic*, *VarξHeteroskedastic*, *VarξClustering*, and *VarξUser*.
