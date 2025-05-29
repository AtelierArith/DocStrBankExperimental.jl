```
XPRS_CPUPLATFORM
```

Newton Barrier: Selects the AMD, Intel x86 or ARM vectorization instruction set that Barrier should run optimized code for. (integer)

On AMD / Intel x86 platforms the SSE2, AVX and AVX2 instruction sets are supported while on ARM platforms the NEON architecture extension can be activated.

Default value: `-2`, using AVX2 instructions if supported by the CPU

Values: -2 : Highest supported [Generic, SSE2, AVX or AVX2]. -1 : Highest supported solve path consistent code [Generic, SSE2 or AVX]. 0 : Use generic code compatible with all CPUs. 1 : Use SSE2 / NEON optimized code. 2 : Use AVX optimized code. 3 : Use AVX2 optimized code.
