Method signature/prototype: `(n::Integer, ::Val{mask})::Nothing where {mask}`.

LLVM will assume that the provided integer `n` has its least significant bits cleared, as specified by the unsigned value `mask`. The latter is passed in the type domain, using `Val`.

!!! danger
    Lying to the compiler is **dangerous**, convincing LLVM that a false statement is true can break your program in subtle ways.

