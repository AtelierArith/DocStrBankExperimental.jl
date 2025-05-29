CUDA.jl's cooperative groups implementation.

Cooperative groups in CUDA offer a structured approach to synchronize and communicate among threads. They allow developers to define specific groups of threads, providing a means to fine-tune inter-thread communication granularity. By offering a more nuanced alternative to traditional CUDA synchronization methods, cooperative groups enable a more controlled and efficient parallel decomposition in kernel design.

The following functionality is available in CUDA.jl:

  * implicit groups: thread blocks, grid groups, and coalesced groups.
  * synchronization: `sync`, `barrier_arrive`, `barrier_wait`
  * warp collectives for coalesced groups: shuffle and voting
  * data transfer: `memcpy_async`, `wait` and `wait_prior`

Noteworthy missing functionality:

  * implicit groups: clusters, and multi-grid groups (which are deprecated)
  * explicit groups: tiling and partitioning
