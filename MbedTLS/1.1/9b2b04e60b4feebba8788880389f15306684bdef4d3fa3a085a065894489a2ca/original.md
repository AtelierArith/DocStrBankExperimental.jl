`digest!(kind::MDKind, msg::Vector{UInt8}, [key::Vector{UInt8}, ], buffer::Vector{UInt8})`

In-place version of `digest` that stores the digest to `buffer`.

It is the user's responsibility to ensure that buffer is long enough to contain the digest. `get_size(kind::MDKind)` returns the appropriate size.
