Set the affinity of a Julia thread to the given CPU-threads.

*Examples:*

  * `setaffinity(socket(1))` # set the affinity to the first socket
  * `setaffinity(numa(2))` # set the affinity to the second NUMA domain
  * `setaffinity(socket(1, 1:3))` # set the affinity to the first three cores in the first NUMA domain
  * `setaffinity([1,3,5])` # set the affinity to the CPU-threads with the IDs 1, 3, and 5.
