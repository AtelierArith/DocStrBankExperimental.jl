[`p8est_lnodes_buffer_t`](@ref) handles the communication of data associated with nodes.

*send_buffers* is an array of arrays: one buffer for each process to which the current process sends node-data. It should not be altered between a shared_*_begin and a shared_*_end call.

*recv_buffers* is an array of arrays that is used in lnodes_share_all_*. *recv_buffers*[j] corresponds with lnodes->sharers[j]: it is the same length as *lnodes*->sharers[j]->shared*nodes. At the completion of lnodes\*share_all or lnodes_share_all_end, recv_buffers[j] contains the node-data from the process lnodes->sharers[j]->rank (unless j is the current rank, in which case recv_buffers[j] is empty).
