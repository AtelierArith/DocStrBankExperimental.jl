Set the affinity of the OpenBLAS thread to the given CPU-threads.

*Examples:*

  * `openblas_setaffinity_cpuids(socket(1))` # set the affinity to the first socket
  * `openblas_setaffinity_cpuids(numa(2))` # set the affinity to the second NUMA domain
  * `openblas_setaffinity_cpuids(socket(1, 1:3))` # set the affinity to the first three cores in the first NUMA domain
  * `openblas_setaffinity_cpuids([1,3,5])` # set the affinity to the CPU-threads with the IDs 1, 3, and 5.
