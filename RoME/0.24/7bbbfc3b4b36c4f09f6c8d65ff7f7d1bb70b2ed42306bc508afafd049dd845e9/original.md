```julia
blockProgress(slam)

```

Block progress on current task until SLAMWrapper is ready to continue taking on more data.

Notes:

  * Use to block addition of more data into slam.dfg object, usually used for preventing duplicate solutions being invoked concurrently.

      * Consider dfg segments: 1. already busy solving, 2. recently added; and now attempting to launch solve on 1&2 before solve on 1. finishes.
  * Also see dead reckon tether (DRT).
  * Assumes unsolved poses are always added and never removed before being solved.

Related

manageSolveTree!, SLAMWrapperLocal
