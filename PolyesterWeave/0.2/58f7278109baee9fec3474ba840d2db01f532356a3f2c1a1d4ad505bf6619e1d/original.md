`request_threads` is called to request a set of `ThreadingUtilities` worker tasks to run on.

```
julia> using PolyesterWeave

julia> PolyesterWeave.request_threads(12)
((Thread (12) Iterator: U[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],), (0x0000000000000fff,))
```

This returns an iterator over the available threads 1-12 `U[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]`, as well as a mask that must be used for freeing these threads when done.

Note that the thread doing the requesting should also always do part of the work. Thus if you want to run on 13 threads, you'd request 12. If you want to run on 8 threads, you'd request 7. Etc.

If you request more threads than available on the system, you get only what is available:

```
julia> Sys.CPU_THREADS, Threads.nthreads()
(16, 8)

julia> r1 = PolyesterWeave.request_threads(30) # Note you get only 7, not 8
((Thread (7) Iterator: U[1, 2, 3, 4, 5, 6, 7],), (0x000000000000007f,))

julia> r2 = PolyesterWeave.request_threads(30)
((Thread (0) Iterator: UInt64[],), (0x0000000000000000,))
```

The following are unsupported features that might be yanked out at any time:

During request you can also mask out which threads you can get. For instance, this call:

```
julia> Sys.CPU_THREADS, Threads.nthreads()
(96, 96)

julia> r1 = PolyesterWeave.request_threads(96, 0xa)
((Thread (2) Iterator: U[2, 4], Thread (31) Iterator: U[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31]), (0x000000000000000a, 0x000000007fffffff))
```

Is saying you want 96 threads, but you have the mask `0x0a` which turns off all threads from the first set of 64 except for 2 and 4:

```
julia> bitstring(0xa)
"00001010"
```

Hence you got the iterator `U[2,4]`, plus an iterator over all the available works from the next batch of 64.
