Function used to encode a single symbol to an [`aws_huffman_code`](@ref)

# Arguments

  * `symbol`:[in] The symbol to encode
  * `userdata`:[in] Optional userdata ([`aws_huffman_symbol_coder`](@ref).userdata)

# Returns

The code representing the symbol. If this symbol is not recognized, return a code with num_bits set to 0.
