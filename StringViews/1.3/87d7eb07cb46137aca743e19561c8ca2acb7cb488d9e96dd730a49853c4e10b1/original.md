This module implements a new type of `AbstractString`, a `StringView`, that provides a string representation of any underlying array of bytes (any `AbstractVector{UInt8}`), interpreted as UTF-8 encoded Unicode data.

Unlike Julia's built-in `String` type (which also wraps UTF-8 data), the `StringView` type is a copy-free wrap of *any* `AbstractVector{UInt8}` instance, and does not take "ownership" of or modify the array.   Otherwise, a `StringView` is intended to be usable in any context where you might have otherwise used `String`.
