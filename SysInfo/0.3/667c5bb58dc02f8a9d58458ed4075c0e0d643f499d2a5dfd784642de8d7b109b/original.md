Returns the CPU IDs of the system as obtained by a round-robin scattering between NUMA domains. Within each NUMA domain, a round-robin ordering among CPU cores is used ("cores before hyperthreads"). Provide `compact=true` to get compact ordering within each NUMA domain. Set `shuffle=true` to randomize.

Optional first argument: Logical indices to select a subset of the sockets.
