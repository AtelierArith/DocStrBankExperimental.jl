```
Status
```

A data structure that stores the status of a quantum computation.  

# Fields

  * `type::String` – One of the declared types, e.g.:

      * "QUEUED"   : Computation in the queue.
      * "RUNNING"  : Computation being processed.
      * "FAILED"   : QPU service has returned an error message.
      * "SUCCEEDED": Computation has succeeded, results are available.
      * "CANCELLED": Computation was terminated before completion.
  * `message::String` – Optional: Message providing additional details about the computation   status.
