```
itercontrol([T=Int], nbits, positions, bit_configs)
```

Returns an iterator which iterate through controlled subspace of bits.

# Example

To iterate through all the bits satisfy `0xx10x1` where `x` means an arbitrary bit.

```jldoctest
julia> for each in itercontrol(7, [1, 3, 4, 7], (1, 0, 1, 0))
           println(string(each, base=2, pad=7))
       end
0001001
0001011
0011001
0011011
0101001
0101011
0111001
0111011

```
