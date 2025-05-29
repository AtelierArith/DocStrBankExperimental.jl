bulkMPO(m)

Generates a bulk matrix product operator with reserved string "O" for zero with a matrix of size `m x m`. Can multiply this object to get bulk MPO for a given system.

# Example:

# Example:

```julia

H = bulkMPO(5) #["O" for i = 1:5,j = 1:5]

#XXZ model
H[1,1] = H[end,end] = "I"
H[2,1] = "S"*Char(0x207B)
H[3,1] = "S"*Char(0x207A)
H[4,1] = "Sz"
H[end,2] = half*"S"*Char(0x207A)
H[end,3] = half*"S"*Char(0x207B)
H[end,4] = "Sz"
H*H*H #multiply 3 sites together

```

See also: [`Omat`](@ref) [`half`](@ref)
