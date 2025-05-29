A multi-qubit Pauli operator ($±\{1,i\}\{I,Z,X,Y\}^{\otimes n}$).

A Pauli can be constructed with the `P` custom string macro or by building up one through products and tensor products of smaller operators.

```jldoctest
julia> pauli3 = P"-iXYZ"
-iXYZ

julia> pauli4 = 1im * pauli3 ⊗ X
+ XYZX

julia> Z*X
+iY
```

We use a typical F(2,2) encoding internally. The X and Z bits are stored in a single concatenated padded array of UInt chunks of a bit array.

```jldoctest
julia> p = P"-IZXY";


julia> p.xz
2-element Vector{UInt64}:
 0x000000000000000c
 0x000000000000000a
```

You can access the X and Z bits through getters and setters or through the `xview`, `zview`, `xbit`, and `zbit` functions.

```jldoctest
julia> p = P"XYZ"; p[1]
(true, false)

julia> p[1] = (true, true); p
+ YYZ
```
