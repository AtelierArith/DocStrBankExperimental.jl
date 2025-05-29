```
ResultStatusCode
```

An Enum of possible values for the `PrimalStatus` and `DualStatus` attributes. The values indicate how to interpret the result vector.

  * `NO_SOLUTION`: the result vector is empty.
  * `FEASIBLE_POINT`: the result vector is a feasible point.
  * `NEARLY_FEASIBLE_POINT`: the result vector is feasible if some constraint tolerances are relaxed.
  * `INFEASIBLE_POINT`: the result vector is an infeasible point.
  * `INFEASIBILITY_CERTIFICATE`: the result vector is an infeasibility certificate. If the `PrimalStatus` is `INFEASIBILITY_CERTIFICATE`, then the primal result vector is a certificate of dual infeasibility. If the `DualStatus` is `INFEASIBILITY_CERTIFICATE`, then the dual result vector is a proof of primal infeasibility.
  * `NEARLY_INFEASIBILITY_CERTIFICATE`: the result satisfies a relaxed criterion for a certificate of infeasibility.
  * `REDUCTION_CERTIFICATE`: the result vector is an ill-posed certificate; see [this article](https://arxiv.org/abs/1408.4685) for details. If the `PrimalStatus` is `REDUCTION_CERTIFICATE`, then the primal result vector is a proof that the dual problem is ill-posed. If the `DualStatus` is `REDUCTION_CERTIFICATE`, then the dual result vector is a proof that the primal is ill-posed.
  * `NEARLY_REDUCTION_CERTIFICATE`: the result satisfies a relaxed criterion for an ill-posed certificate.
  * `UNKNOWN_RESULT_STATUS`: the result vector contains a solution with an unknown interpretation.
  * `OTHER_RESULT_STATUS`: the result vector contains a solution with an interpretation not covered by one of the statuses defined above.
