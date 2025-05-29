```julia
struct ExtendedJumpArray{T3<:Number, T1, T<:AbstractArray{T3<:Number, T1}, T2} <: AbstractArray{T3<:Number, 1}
```

Extended state definition used within integrators when there are `VariableRateJump`s in a system. For detailed examples and usage information, see the

  * [Tutorial](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)

### Fields

  * `u`: The current state.
  * `jump_u`: The current rate (i.e. hazard, intensity, or propensity) values for the `VariableRateJump`s.

## Examples

```julia
using JumpProcesses, OrdinaryDiffEq
f(du,u,p,t) = du .= 0
rate(u,p,t) = (1+t)*u[1]*u[2]

# suppose we wish to decrease each of the two variables by one
# when a jump occurs
function affect!(integrator)
   # Method 1, direct indexing works like normal
   integrator.u[1] -= 1
   integrator.u[2] -= 1

   # Method 2, if we want to broadcast or use array operations we need
   # to access integrator.u.u which is the actual state object.
   # So equivalently to above we could have said:
   # integrator.u.u .-= 1
end

u0 = [10.0, 10.0]
vrj = VariableRateJump(rate, affect!)
oprob = ODEProblem(f, u0, (0.0,2.0))
jprob = JumpProblem(oprob, Direct(), vrj)
sol = solve(jprob,Tsit5())
```

## Notes

  * If `ueja isa ExtendedJumpArray` with `ueja.u` of size `N` and `ueja.jump_u` of size `num_variableratejumps` then

    ```julia
    # for 1 <= i <= N
    ueja[i] == ueja.u[i]

    # for N < i <= (N+num_variableratejumps)
    ueja[i] == ueja.jump_u[i]
    ```
  * In a system with `VariableRateJump`s all callback, `ConstantRateJump`, and `VariableRateJump` `affect!` functions will receive integrators with `integrator.u` an `ExtendedJumpArray`.
  * As such, `affect!` functions that wish to modify the state via vector operations should use `ueja.u.u` to obtain the aliased state object.
