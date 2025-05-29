```
minkowski_dot(v1,v2)
```

2つの `LorentzVectorLike` のミンコフスキー内積を返します。

!!! example
    `(t1,x1,y1,z1)` と `(t2,x2,y2,z2)` が2つの `LorentzVectorLike` である場合、これは次のように等価です。

    ```julia
    t1*t2 - (x1*x2 + y1*y2 + z1*z2)
    ```


!!! note
    我々は主にマイナスの計量を使用します。

