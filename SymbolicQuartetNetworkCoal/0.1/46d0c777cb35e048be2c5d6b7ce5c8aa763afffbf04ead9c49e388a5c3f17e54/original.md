```
readTopologyrand(net; scaleparameter=1.0, dpoints=7)
```

Generates randomized values for all edge lengths and inheritance probabilities in the input network.

## Description

The input network can be provided as either a Newick/Extended Newick string or a PhyloNetworks `HybridNetwork` object,  with or without parameters specified. The function assumes a **binary network** and produces a **non-ultrametric network**.

  * Edge lengths are determined using:   `scaleparameter * (edge.number + random value in [0,1])`   The `scaleparameter` defaults to `1.0`.
  * Inheritance probabilities (gamma values) are assigned random values in the range (0,1).

**Caution:**   This function does **not** simulate realistic parameters in an empty network topology.  This function is not intended to simulate parameters with biological background. Instead, it assigns **dummy** values to allow the topology to be processed by downstream functions.

## Arguments

  * `net`: The input network (Newick string, file containing Newick, or a `HybridNetwork` object).
  * `scaleparameter`: Multiplier applied to the generated edge lengths. Defaults to `1.0`.
  * `dpoints`: Number of decimal places for rounding. Defaults to `7`.

## Returns

  * A PhyloNetworks `HybridNetwork` object with randomly assigned edge lengths and inheritance probabilities.
