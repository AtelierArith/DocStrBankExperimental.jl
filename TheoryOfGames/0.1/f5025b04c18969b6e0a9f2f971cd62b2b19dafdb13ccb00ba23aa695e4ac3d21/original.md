```
IterMode is a structure defining the modality for interative identification
of the benefit distribution mechanism
```

## Fields

player*set     Vector of players callback*benefit*by*coalition : Function     Callback function that is used to determine what is the benefit of a coalition     and the total benefit of the coalition callback*worst*coalition : Function     Callback function that is used to determine what is the coalition with the worst benefit     and the total benefit of the coalition.     Arguments shall be:     - (mandatory) a Dict-like container to describe the current reward distribution by user     - kwargs (optional):         - modify*solver*options: vector of pairs to iteratively change the optimization callback             to speed up computation time. The implemented callbacks are:             1. best*obj*stop: when the best*obj*stop callback is used in iterative methods,                 the corresponding option is updated here depending on the value             2. lower*relaxation*stop*option: option to stop the execution as a lower bound is reached     The function shall return a Vector of NamedTuple, where for every entry o shall contain:     - least*profitable*coalition: members of the worst coalition, for result o     - coalition*benefit: benefit of the coalition, for result o     - min_surplus: minimum surplus of the coalition, for result o
