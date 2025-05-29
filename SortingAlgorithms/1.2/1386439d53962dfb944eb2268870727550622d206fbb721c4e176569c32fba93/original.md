```
PagedMergeSort
```

Indicates that a sorting function should use the paged merge sort algorithm. Paged merge sort uses is a merge sort, that uses different merge routines to achieve stable sorting with a scratch space of size O(√n). The merge routine for merging large subarrays merges pages of size O(√n) almost in place, before reordering them using a page table. At deeper recursion levels, where the scratch space is big enough, normal merging is used, where one input is copied into the scratch space. When the scratch space is large enough to hold the complete subarray, the input is merged interleaved from both sides, which increases performance for random data.

Characteristics:

  * *stable*: does preserve the ordering of elements which compare equal (e.g. "a" and "A" in a sort of letters which ignores case).
  * *`O(√n)`* auxilary memory usage.
  * *`O(n log n)`* garuanteed runtime.

## References

  * Dvořák, S., Ďurian, B. (1986). Towards an efficient merging. In: Gruska, J., Rovan, B., Wiedermann, J. (eds) Mathematical Foundations of Computer Science 1986. MFCS 1986. Lecture Notes in Computer Science, vol 233. Springer, Berlin, Heidelberg. https://doi.org/10.1007/BFb0016253
  * https://max-arbuzov.blogspot.com/2021/10/merge-sort-with-osqrtn-auxiliary-memory.html
