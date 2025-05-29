```
ClassData(type, s₁, s₂, s₃)
```

Based on the input `type`, generates 3 classes of signals with sample sizes `s₁`, `s₂`, and `s₃` respectively. Accepted input types are:  

  * `:tri`: Triangular signals of length 32
  * `:cbf`: Cylinder-Bell-Funnel signals of length 128

Based on N. Saito and R. Coifman in "Local Discriminant Basis and their Applications" in the Journal of Mathematical Imaging and Vision, Vol. 5, 337-358 (1995).

**See also:** [`generateclassdata`](@ref)
