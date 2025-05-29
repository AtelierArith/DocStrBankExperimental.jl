Method signature/prototype: `(condition::Bool)::Nothing`.

LLVM will assume that the provided argument will be `true`, in any possible execution of your program.

!!! danger
    Lying to the compiler is **dangerous**, convincing LLVM that a false statement is true can break your program in subtle ways.

