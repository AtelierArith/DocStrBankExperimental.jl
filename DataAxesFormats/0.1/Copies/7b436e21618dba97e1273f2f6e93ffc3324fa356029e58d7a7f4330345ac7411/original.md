Copy data between `Daf` data sets.

!!! note
    Copying into an in-memory data set does **not** duplicate the data; instead it just shares a reference to it. This is fast. In contrast, copying into a disk-based data set (e.g. using HDF5 or simple files) **will** create a duplicate of the data on disk. This is slow. However, both directions will not significantly increase the amount of memory allocated by the application.

