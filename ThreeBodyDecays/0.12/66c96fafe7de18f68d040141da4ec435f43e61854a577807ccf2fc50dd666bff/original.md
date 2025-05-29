ThreeBodyDecay(; chains, couplings, names)

Constructs a `ThreeBodyDecay` object with the given parameters.

# Arguments

  * `chains`: An array of chains involved in the decay. The length of this array should match the lengths of `couplings` and `names`.
  * `couplings`: An array of coupling constants for each chain in the decay. The length of this array should match the lengths of `chains` and `names`.
  * `names`: An array of names for each chain, or names of resonances in the decay. The length of this array should match the lengths of `chains` and `couplings`.

# Returns

  * A `ThreeBodyDecay` object with the specified chains, couplings, and names.

# Examples

```julia
ThreeBodyDecay(
chains=[chain1, chain2, chain3],
couplings=[1.0, -1.0, 0.2im],
names=["L1405", "L1405", "K892"])
```
