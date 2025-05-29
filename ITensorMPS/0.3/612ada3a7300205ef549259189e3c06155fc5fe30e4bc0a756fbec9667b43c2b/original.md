```
noiseterm(P::ProjMPOSum,
          phi::ITensor,
          ortho::String)
```

Return a "noise term" or density matrix perturbation ITensor as proposed in Phys. Rev. B 72, 180403 for aiding convergence of DMRG calculations. The ITensor `phi` is the contracted product of MPS tensors acted on by the ProjMPOSum `P`, and `ortho` is a String which can take the values `"left"` or `"right"` depending on the sweeping direction of the DMRG calculation.
