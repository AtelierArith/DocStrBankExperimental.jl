```
value(g::Group)::Union{BigInt, Tuple{BigInt, BigInt}, Tuple{BitVector, BitVector}}
```

Converts the group instance to the most simple representation. Generally intended for debugging purposes and for serialization one should use `octet` as it also ensures consistent padding. 

See also `octet`, `Curves.gx`, `Curves.gy`
