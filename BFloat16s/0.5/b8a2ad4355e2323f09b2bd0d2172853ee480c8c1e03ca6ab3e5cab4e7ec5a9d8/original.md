LowPrecArray

An n-dimensional array that behaves essentially like a Float32 array for all scalar operations, but matmuls are performed in BFloat16 with Float32 accumulation. This is intended to match the behavior of TPUs.
