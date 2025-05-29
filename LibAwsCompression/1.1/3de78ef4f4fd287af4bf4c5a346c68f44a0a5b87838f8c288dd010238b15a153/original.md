Function used to decode a code into a symbol

# Arguments

  * `bits`:[in] The bits to attept to decode a symbol from
  * `symbol`:[out] The symbol found. Do not write to if no valid symbol found
  * `userdata`:[in] Optional userdata ([`aws_huffman_symbol_coder`](@ref).userdata)

# Returns

The number of bits read from bits
