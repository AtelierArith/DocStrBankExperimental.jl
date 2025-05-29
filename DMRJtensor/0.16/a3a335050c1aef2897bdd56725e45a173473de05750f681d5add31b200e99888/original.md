```
mpo = makeMPO(H,physSize,Ns[,lower=])
```

Converts a bulk MPO tensor `H` into an MPO `mpo` of `Ns` sites; `physSize` is a number (uniform sites); `lower` signifies the input is the lower triangular form (default) and is represented by a tensor diagrammatically as

```
     s2
     |
```

a1 – W – a2       =    W[a1,s1,s2,a2]          |          s1

# Example:

```julia
spinmag = 0.5;Ns = 10
Sp,Sm,Sz,Sx,Sy,O,Id = spinOps(spinmag)
function H(i::Integer)
    return [Id O O;
            Sz O O;
            O Sz Id]
end
isingmpo = makeMPO(H,size(Id,1),Ns)
```
