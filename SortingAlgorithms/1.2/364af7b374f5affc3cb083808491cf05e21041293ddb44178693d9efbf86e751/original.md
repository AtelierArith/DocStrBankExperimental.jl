```
CombSort
```

Indicates that a sorting function should use the comb sort algorithm. Comb sort traverses the collection multiple times ordering pairs of elements with a given interval between them. The interval decreases exponentially until it becomes 1, then it switches to insertion sort on the whole input.

Characteristics:

  * *not stable* does not preserve the ordering of elements which compare equal (e.g. "a" and "A" in a sort of letters which ignores case).
  * *in-place* in memory.
  * *parallelizable* suitable for vectorization with SIMD instructions because it performs many independent comparisons.
  * *pathological inputs* such as `repeat(1:5.0, 4^8)` can make this algorithm perform very poorly.
  * *`n log n` average runtime* measured for random inputs of length up to 100 million, but theoretical runtime of `Θ(n^2)` for extremely long inputs.

## References

  * Dobosiewicz, Wlodzimierz, (1980). "An efficient variation of bubble sort", Information Processing Letters, 11(1), pp. 5-6, https://doi.org/10.1016/0020-0190(80)90022-8.
  * Werneck, N. L., (2020). "ChipSort: a SIMD and cache-aware sorting module. JuliaCon Proceedings, 1(1), 12, https://doi.org/10.21105/jcon.00012
  * H. Inoue, T. Moriyama, H. Komatsu and T. Nakatani, "AA-Sort: A New Parallel Sorting Algorithm for Multi-Core SIMD Processors," 16th International Conference on Parallel Architecture and Compilation Techniques (PACT 2007), 2007, pp. 189-198, doi: 10.1109/PACT.2007.4336211.
