```
fidelity(A::ITensor, B::ITensor)
```

Compute the quantum fidelity between two ITensors. Wrap each one in the ITensorState and the ITensorOperator according to the index structure to allow dispatch.
