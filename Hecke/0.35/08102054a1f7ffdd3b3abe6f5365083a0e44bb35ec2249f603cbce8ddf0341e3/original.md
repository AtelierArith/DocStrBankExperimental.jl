```
rational_reconstruction(A::SRow{ZZRingElem}, M::ZZRingElem) -> Bool, SRow{ZZRingElem}, ZZRingElem
```

Apply rational reconstruction to the entries of $A$. Returns true iff successful. In this case, the numerator is returned as a matrix and the common denominator in the third value.
