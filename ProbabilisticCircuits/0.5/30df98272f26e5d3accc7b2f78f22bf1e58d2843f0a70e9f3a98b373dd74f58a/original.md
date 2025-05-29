```
MAP(pc::ProbCircuit, data::Matrix; batch_size, Float=Float32)
```

Evaluate max a posteriori (MAP) state of the circuit for given input(s) on cpu.

**Note**: This algorithm is only exact if the circuit is both decomposable and determinisitic. If the circuit is only decomposable and not deterministic, this will give inexact results without guarantees.
