```
approximatefekete(basis, samples; base_ring=BigFloat) -> basis, samples
```

Compute approximate fekete points based on samples and a corresponding orthogonal basis. The basis consists of sampled polynomials, sampled at `samples`.

This preserves a degree ordering of `basis` if present.
