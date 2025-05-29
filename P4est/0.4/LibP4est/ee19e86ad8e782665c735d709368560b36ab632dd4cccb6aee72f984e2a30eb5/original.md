```
p8est_find_partition(num_procs, search_in, my_begin, my_end, _begin, _end)
```

Binary search in partition array. Given two targets *my_begin* and *my_end*, find offsets such that `search\_in[begin] >= my\_begin`, `my\_end <= search\_in[end]`. If more than one index satisfies the conditions, then the minimal index is the result. If there is no index that satisfies the conditions, then *begin* and *end* are tried to set equal such that `search\_in[begin] >= my\_end`. If *my_begin* is less or equal than the smallest value of *search_in* *begin* is set to 0 and if *my_end* is bigger or equal than the largest value of *search_in* *end* is set to *num_procs* - 1. If none of the above conditions is satisfied, the output is not well defined. We require `my_begin <= my_begin'.

### Parameters

  * `num_procs`:[in] Number of processes to get the length of *search_in*.
  * `search_in`:[in] The sorted array (ascending) in that the function will search. If `k` indexes search_in, then `0 <= k < num\_procs`.
  * `my_begin`:[in] The first target that defines the start of the search window.
  * `my_end`:[in] The second target that defines the end of the search window.
  * `begin`:[in,out] The first offset such that `search\_in[begin] >= my\_begin`.
  * `end`:[in,out] The second offset such that `my\_end <= search\_in[end]`.

### Prototype

```c
void p8est_find_partition (const int num_procs, p4est_gloidx_t * search_in, p4est_gloidx_t my_begin, p4est_gloidx_t my_end, p4est_gloidx_t * begin, p4est_gloidx_t * end);
```
