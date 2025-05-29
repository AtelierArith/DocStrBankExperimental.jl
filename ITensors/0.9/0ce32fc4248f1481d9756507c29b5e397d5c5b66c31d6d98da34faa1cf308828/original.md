```
apply(A::ITensor, B::ITensor)
(A::ITensor)(B::ITensor)
product(A::ITensor, B::ITensor)
```

Get the product of ITensor `A` and ITensor `B`, which roughly speaking is a matrix-matrix product, a matrix-vector product, or a vector-matrix product, depending on the index structure.

There are three main modes:

1. Matrix-matrix product. In this case, ITensors `A`

and `B` have shared indices that come in pairs of primed and unprimed indices. Then, `A` and `B` are multiplied together, treating them as matrices from the unprimed to primed indices, resulting in an ITensor `C` that has the same pairs of primed and unprimed indices. For example:

```
s1'-<-----<-s1            s1'-<-----<-s1   s1'-<-----<-s1
      |C|      = product(       |A|              |B|      )
s2'-<-----<-s2            s2'-<-----<-s2 , s2'-<-----<-s2
```

Essentially, this is implemented as `C = mapprime(A', B, 2 => 1)`. If there are dangling indices that are not shared between `A` and `B`, a "batched" matrix multiplication is performed, i.e.:

```
       j                         j
       |                         |
s1'-<-----<-s1            s1'-<-----<-s1   s1'-<-----<-s1
      |C|      = product(       |A|              |B|      )
s2'-<-----<-s2            s2'-<-----<-s2 , s2'-<-----<-s2
```

In addition, if there are shared dangling indices, they are summed over:

```
                                    j                j
                                    |                |
s1'-<-----<-s1               s1'-<-----<-s1   s1'-<-----<-s1
      |C|      = Σⱼ product(       |A|              |B|      )
s2'-<-----<-s2               s2'-<-----<-s2 , s2'-<-----<-s2
```

where the sum is not performed as an explicitly for-loop, but as part of a single tensor contraction.

2. Matrix-vector product. In this case, ITensor `A`

has pairs of primed and unprimed indices, and ITensor `B` has unprimed indices that are shared with `A`. Then, `A` and `B` are multiplied as a matrix-vector product, and the result `C` has unprimed indices. For example:

```
s1-<----            s1'-<-----<-s1   s1-<----
     |C| = product(       |A|             |B| )
s2-<----            s2'-<-----<-s2 , s2-<----
```

Again, like in the matrix-matrix product above, you can have dangling indices to do "batched" matrix-vector products, or sum over a batch of matrix-vector products.

3. Vector-matrix product. In this case, ITensor `B`

has pairs of primed and unprimed indices, and ITensor `A` has unprimed indices that are shared with `B`. Then, `B` and `A` are multiplied as a matrix-vector product, and the result `C` has unprimed indices. For example:

```
---<-s1            ----<-s1   s1'-<-----<-s1
|C|     = product( |A|              |B|      )
---<-s2            ----<-s2 , s2'-<-----<-s2
```

Again, like in the matrix-matrix product above, you can have dangling indices to do "batched" vector-matrix products, or sum over a batch of vector-matrix products.

4. Vector-vector product. In this case, ITensors `A`

and `B` share unprimed indices. Then, `B` and `A` are multiplied as a vector-vector product, and the result `C` is a scalar ITensor. For example:

```
---            ----<-s1   s1-<----
|C| = product( |A|             |B| )
---            ----<-s2 , s2-<----
```

Again, like in the matrix-matrix product above, you can have dangling indices to do "batched" vector-vector products, or sum over a batch of vector-vector products.
