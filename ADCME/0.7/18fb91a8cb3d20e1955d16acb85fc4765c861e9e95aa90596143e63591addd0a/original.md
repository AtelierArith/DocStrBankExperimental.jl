```
compress(A::SparseTensor)
```

Compresses the duplicated index in `A`. 

# Example

```julia
using ADCME
indices = [
    1 1 
    1 1
    2 2
    3 3
]
v = [1.0;1.0;1.0;1.0]
A = SparseTensor(indices[:,1], indices[:,2], v, 3, 3)
Ac = compress(A)
sess = Session(); init(sess)

run(sess, A.o.indices) # expected: [0 0;0 0;1 1;2 2]
run(sess, A.o.values) # expected: [1.0;1.0;1.0;1.0]


run(sess, Ac.o.indices) # expected: [0 0;1 1;2 2]
run(sess, Ac.o.values) # expected: [2.0;1.0;1.0]
```

!!! note
    The indices of `A` should be sorted. `compress` does not check the validity of the input arguments.

