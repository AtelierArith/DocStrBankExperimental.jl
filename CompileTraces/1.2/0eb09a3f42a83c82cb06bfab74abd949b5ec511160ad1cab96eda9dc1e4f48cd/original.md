Object used to track various metrics related to compilation successes and failures for later introspection.

For example, you might want to test or assert that all or at least a certain number of traces were successfully compiled.

Public fields:

  * `succeeded`: the number of statements that successfully compiled.
  * `failed`: the number of statements that failed to compile.
  * `skipped`: the number of statements that were avoided due to limitations in compilation. This should be very rare, and related to overloaded `Vararg` or despecialized arguments.
  * `total`: the number of statements that were processed. This is the sum of all three other fields.
