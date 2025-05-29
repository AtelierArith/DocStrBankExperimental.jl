A diagonal representation of Bell diagonal states that only tracks the phases in front of the stabilizers tableau instead of the whole stabilizer tableau.

Capable of representing only tensor products of one or more of the states

```
±XX
±ZZ
```

by tracking only the phases in the first column. For example, `XX -ZZ` is represented as the bitstring `01`.

This representation permits drastically faster simulation of entanglement purification circuits.

The `BellState(n)` constructor will create `n` Bell pairs.

```jldoctest
julia> bell_state = BellState([0,1,1,0])
BellState(Bool[0, 1, 1, 0])

julia> Stabilizer(bell_state)
+ XX__
- ZZ__
- __XX
+ __ZZ
```

As mentioned above, we can represent only Bell states. Here is the basis being used:

| `BPGates` notation | Stabilizer tableaux | Kets        | in X basis  | in Y basis      |
|:------------------ |:------------------- |:----------- |:----------- |:--------------- |
| `00`               | `+XX +ZZ`           | `∣00⟩+∣11⟩` | `∣++⟩+∣--⟩` | `∣i₊i₋⟩+∣i₋i₊⟩` |
| `01`               | `+XX -ZZ`           | `∣01⟩+∣10⟩` | `∣++⟩-∣--⟩` | `∣i₊i₊⟩-∣i₋i₋⟩` |
| `10`               | `-XX +ZZ`           | `∣00⟩-∣11⟩` | `∣+-⟩+∣-+⟩` | `∣i₊i₊⟩+∣i₋i₋⟩` |
| `11`               | `-XX -ZZ`           | `∣01⟩-∣10⟩` | `∣+-⟩-∣-+⟩` | `∣i₊i₋⟩-∣i₋i₊⟩` |

You can convert between these descriptions using

  * `BPGates` to stabilizer state with `QuantumClifford.Stabilizer(bpgates_state)`
  * stabilizer state to ket with `QuantumOptics.Ket`
