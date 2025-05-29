```
XPRSnlpvalidatekkt(prob, mode, respectbasis, updatemult, violtarget)::prob
```

Validates the first order optimality conditions also known as the Karush-Kuhn-Tucker (KKT) conditions versus the currect solution

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `mode::Integer`: The calculation mode can be: 0recalculate the reduced costs at the current solution using the current dual solution.
  * `respectbasis::Integer`: The following ways are defined to assess if a constraint is active: 0evaluate the recalculated slack activity versus XSLP*ECFTOL*R.
  * `updatemult::Integer`: The calculated values can be: 0only used to calculate the XSLP*VALIDATIONINDEX*K measure.
  * `violtarget::Float64`: When calculating the best KKT multipliers, it is possible to enforce an even distribution of reduced costs violations by enforcing a bound on them.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSnlpvalidatekkt](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpvalidatekkt.html) in the C API.
