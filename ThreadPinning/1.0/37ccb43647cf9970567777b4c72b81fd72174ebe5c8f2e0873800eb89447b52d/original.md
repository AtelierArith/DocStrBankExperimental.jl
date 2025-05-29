Unpin all threads on all Julia workers.

If `include_master=true`, the master process (`Distributed.myid() == 1`) will be unpinned as well.
