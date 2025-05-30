@unroll expr

Takes a for loop as `expr` and informs the LLVM unroller to fully unroll it, if it is safe to do so and the loop count is known.
