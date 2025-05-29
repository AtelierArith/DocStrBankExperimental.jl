Variable represents a reference to an operation on a tape. Variables can be used to index tape or keep reference to a specific operation on the tape.

Variables (also aliesed as `V`) can be:

  * free, created as `V(id)` - used for indexing into tape
  * bound, created as `V(op)` or V(tape, id) - used to keep a robust reference to an operation on the tape

See also: [`bound`](@ref)
