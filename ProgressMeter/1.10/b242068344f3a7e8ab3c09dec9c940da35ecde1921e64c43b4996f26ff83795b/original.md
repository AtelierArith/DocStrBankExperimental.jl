`ProgressMeter` contains a suite of utilities for displaying progress in long-running computations. The major functions/types in this module are:

  * `@showprogress`: an easy interface for straightforward situations
  * `Progress`: an object for managing progress updates with a predictable number of iterations
  * `ProgressThresh`: an object for managing progress updates where termination is governed by a threshold
  * `next!` and `update!`: report that progress has been made
  * `cancel` and `finish!`: early termination
