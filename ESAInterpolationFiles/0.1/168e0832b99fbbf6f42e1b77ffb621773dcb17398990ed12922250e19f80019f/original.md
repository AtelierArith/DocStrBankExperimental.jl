```
IPF{C, V}
```

Struct to store ESA/ESOC Interpolation File data.

  * `filepath::String`: The path to the IPF file.
  * `header::IPFHeader`: The header information of the IPF file.
  * `blocks::Vector{IPFBlockInfo}`: Information about the blocks within the IPF file.
  * `first_key::V`: The first key value stored in the IPF file.
  * `last_key::V`: The last key value stored in the IPF file.
  * `array::Vector{UInt8}`: An array containing the binary data of the IPF file.
  * `cache::InterpCache{C, V}`: Cache for interpolation data.

Here the parameters are the cache-type `C` and the value type `V`.

## Constructors

  * `IPF{C, V}(filepath::String)`: Constructs an `IPF` object from the specified file path,    with the option to specify the types for cache (`C`) and values (`V`).
  * `IPF(filepath::String)`: Constructs an `IPF` object with default types    `Float64` for both cache and values.
