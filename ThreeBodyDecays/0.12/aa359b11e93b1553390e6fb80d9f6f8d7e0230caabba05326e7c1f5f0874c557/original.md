ThreeBodyDecay(descriptor)

Constructs a `ThreeBodyDecay` object using one argument, a descriptor. The `descriptor` is a list of pairs, `names .=> zip(couplings, chains)`.

# Examples

```julia
ThreeBodyDecay("K892" .=> zip([1.0, -1.0, 0.2im], [chain1, chain2, chain3]))
```
