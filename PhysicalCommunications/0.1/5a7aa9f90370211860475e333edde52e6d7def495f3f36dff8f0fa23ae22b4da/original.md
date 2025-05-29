```
sequence(t::SequenceGenerator; seed::Integer=11, len::Int=-1, output::DataType=Int)
```

Create an iterable object that defines a bit sequence of length `len`.

Inputs:

  * t: Instance defining type of algorithm used to generate bit sequence.
  * seed: Initial value of register used to build sequence.
  * len: Number of bits in sequence.
  * output: DataType used for sequence elements (typical values are `Int` or `Bool`).

Example returning the first `1000` bits of a PRBS-`31` pattern constructed with the Maximum-length LFSR algorithm seeded with an initial register value of `11`.:

```
pattern = collect(sequence(MaxLFSR(31), seed=11, len=1000, output=Bool)).
```
