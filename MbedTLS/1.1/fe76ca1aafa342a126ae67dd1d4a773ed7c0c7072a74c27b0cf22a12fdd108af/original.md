`digest(kind::MDKind, msg::Vector{UInt8}, [key::Vector{UInt8}]) -> Vector{UInt8}`

Perform a digest of the given type on the given message (a byte array), return a byte array with the digest.

If an optional key is given, perform an HMAC digest.
