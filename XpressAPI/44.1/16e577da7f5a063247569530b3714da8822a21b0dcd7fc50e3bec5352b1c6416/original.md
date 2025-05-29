```
XPRSaddcbusersolnotify(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `usersolnotify`.
  * `solname`: The string name assigned to the solution when it was loaded into the Optimizer using XPRSaddmipsol.
  * `status`: One of the following status values: 0An error occurred while processing the solution. (`XPRS_USERSOLSTATUS_ERROR`) 1Solution is feasible. (`XPRS_USERSOLSTATUS_ACCEPTED_FEASIBLE`) 2Solution is feasible after reoptimizing with fixed MIP entities. (`XPRS_USERSOLSTATUS_ACCEPTED_OPTIMIZED`) 3A local search heuristic was applied and a feasible solution discovered. (`XPRS_USERSOLSTATUS_SEARCHED_SOL`) 4A local search heuristic was applied but a feasible solution was not found. (`XPRS_USERSOLSTATUS_SEARCHED_NOSOL`) 5Solution is infeasible and a local search could not be applied. (`XPRS_USERSOLSTATUS_REJECTED_INFEAS_NOSEARCH`) 6Solution is partial and a local search could not be applied. (`XPRS_USERSOLSTATUS_REJECTED_PARTIAL_NOSEARCH`) 7Failed to reoptimize the problem with MIP entities fixed to the provided solution. Likely because a time or iteration limit was reached. (`XPRS_USERSOLSTATUS_REJECTED_FAILED_OPTIMIZE`) 8Solution is dropped. This can happen if the MIP problem is changed or solved to completion before the solution could be processed. (`XPRS_USERSOLSTATUS_DROPPED`) 9The solution is worse than the current MIP cutoff value. (`XPRS_USERSOLSTATUS_REJECTED_CUTOFF`)

`cb` will be invoked with this signature:

```
cb(cbprob, solname, status)::Nothing
```
