Method signature/prototype: `()::Union{}` (meaning: call without arguments, assumed never to return).

LLVM will assume that any call of this function will *never* be reached in any execution of your code. In other words, the call is assumed to be *unreachable*.

!!! danger
    Lying to the compiler is **dangerous**, convincing LLVM that a false statement is true can break your program in subtle ways.

