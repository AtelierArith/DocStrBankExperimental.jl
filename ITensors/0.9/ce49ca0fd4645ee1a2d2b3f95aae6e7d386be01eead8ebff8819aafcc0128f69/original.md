ITensor is a library for rapidly creating correct and efficient tensor network algorithms.

An ITensor is a tensor whose interface is independent of its memory layout. ITensor indices are 'intelligent' meaning they carry extra information and 'recognize' each other automatically when contracting or adding ITensors.

The ITensor library includes composable and extensible algorithms for optimizing and transforming tensor networks, such as matrix product state and matrix product operators.

# Example Usage

Define tensor indices i and j

```
i = Index(2, "i")
j = Index(3, "j")
```

Make an ITensor with these indices

```
A = ITensor(i,j)
```

Set the i==2,j==1 element to -2.6

```
A[j=>1,i=>2] = -2.6
A[i=>2,j=>1] = -2.6 #this has the same effect
```

Make an ITensor with random elements

```
B = random_itensor(j,i)
```

Add ITensors A and B together (ok that indices in different order)

```
C = A + B
```

# Other Features of ITensor

  * Tools for **tensor networks**, such as matrix product states (MPS) / tensor trains (TT)
  * **Algorithms** for solving linear equations in MPS form (such as DMRG) or for integrating differential equations ("time evolving MPS")
  * ITensors can have **sparse data** internally, such as block sparsity or diagonal sparsity, while having the same interface as dense ITensors
  * ITensors can have **symmetry properties** (invariance or equivariance) under group transformations of the indices. In physics terminology such ITensors conserve quantum numbers.

# Documentation and Resources

ITensor website: https://itensor.org/

Documentation: https://itensor.github.io/ITensors.jl/stable/
