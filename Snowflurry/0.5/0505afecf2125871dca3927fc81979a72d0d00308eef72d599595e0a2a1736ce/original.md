```
get_destination_bit(readout::Readout)::Int
```

Returns the index of the classical bit to which the outcome of the `readout` is sent.

# Examples

```jldoctest
julia> get_destination_bit(readout(2, 3))
3

```
