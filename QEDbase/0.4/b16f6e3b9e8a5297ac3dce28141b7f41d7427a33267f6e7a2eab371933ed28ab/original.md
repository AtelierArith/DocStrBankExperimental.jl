```
minkowski_dot(v1,v2)
```

Return the Minkowski dot product of two `LorentzVectorLike`.

!!! example
    If `(t1,x1,y1,z1)` and `(t2,x2,y2,z2)` are two `LorentzVectorLike`, this is equivalent to

    ```julia
    t1*t2 - (x1*x2 + y1*y2 + z1*z2)
    ```


!!! note
    We use the mostly minus metric.

