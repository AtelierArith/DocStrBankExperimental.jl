```
onehot(ivs...)
setelt(ivs...)
onehot(::Type, ivs...)
setelt(::Type, ivs...)
```

Create an ITensor with all zeros except the specified value, which is set to 1.

# Examples

```julia
i = Index(2,"i")
A = onehot(i=>2)
# A[i=>2] == 1, all other elements zero

# Specify the element type
A = onehot(Float32, i=>2)

j = Index(3,"j")
B = onehot(i=>1,j=>3)
# B[i=>1,j=>3] == 1, all other element zero
```
