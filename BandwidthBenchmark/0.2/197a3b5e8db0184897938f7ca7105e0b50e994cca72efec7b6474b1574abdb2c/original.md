Similar to `bwscaling` but measures the memory bandwidth scaling within and across memory domains. Returns a `DataFrame` in which each row contains the kernel name, the number of threads per memory domain, the number of domains considered, and the measured memory bandwidth (in MB/s).

**Keyword arguments**

  * `domains`: memory domains to consider (logical indices, i.e. starting at 1)
  * `max_nthreads`: maximal number of threads per memory domain to consider
