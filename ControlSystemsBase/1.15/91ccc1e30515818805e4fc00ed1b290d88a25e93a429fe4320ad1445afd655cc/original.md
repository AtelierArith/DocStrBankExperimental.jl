```
C = pid_2dof(param_p, param_i, [param_d]; form=:standard, state_space=true, N = 10, [Ts], b=1, c=0, disc=:tustin)
```

Calculates and returns a PID controller on 2DOF form with inputs `[r; y]` and outputs `u` where `r` is the reference signal, `y` is the measured output and `u` is the control signal.

Belowm we show two different depections of the contorller, one as a 2-input system (left) and one where the tw internal SISO systems of the controller are shown (right).

```
                                ┌──────┐                      
                             r  │      │                      
                            ───►│  Cr  ├────┐                 
r  ┌─────┐     ┌─────┐          │      │    │    ┌─────┐      
──►│     │  u  │     │ y        └──────┘    │    │     │ y    
   │  C  ├────►│  P  ├─┬─►                  +───►│  P  ├─┬───►
 ┌►│     │     │     │ │        ┌──────┐    │    │     │ │    
 │ └─────┘     └─────┘ │      y │      │    │    └─────┘ │    
 │                     │     ┌─►│  Cy  ├────┘            │    
 └─────────────────────┘     │  │      │                 │    
                             │  └──────┘                 │    
                             │                           │    
                             └───────────────────────────┘     
```

The `form` can be chosen as one of the following (determines how the arguments `param_p, param_i, param_d` are interpreted)

  * `:standard` - $K_p(br-y + (r-y)/(T_i s) + T_d s (cr-y)/(T_f s + 1))$
  * `:parallel` - $K_p(br-y) + K_i (r-y)/s + K_d s (cr-y)/(Tf s + 1)$
  * `b` is a set-point weighting for the proportional term
  * `c` is a set-point weighting for the derivative term, this defaults to 0.
  * If both `b` and `c` are set to zero, the feedforward path of the controller will be strictly proper.
  * `Tf` is a time constant for a filter on the derivative term, this defaults to `Td/N` where `N` is set to 10. Instead of passing `Tf` one can also pass `N` directly. The proportional term is not affected by this filter. **Please note**: this derivative filter is not the same as the one used in the `pid` function, where the filter is of second order and applied in series with the contorller, i.e., it affects all three PID terms.
  * A PD controller is constructed by setting `param_i` to zero.
  * A balanced state-space realization is returned, unless `balance = false`
  * If `Ts` is supplied, the controller is discretized using the method `disc` (defaults to `:tustin`).

This controller has negative feedback built in, and the closed-loop system from `r` to `y` is thus formed as

```
Cr, Cy = C[1, 1], C[1, 2]
feedback(P, Cy, pos_feedback=true)*Cr                    # Alternative 1
feedback(P, -Cy)*Cr                                      # Alternative 2
feedback(P, C, U2=2, W2=1, W1=[], pos_feedback=true) # Alternative 3, less pretty but more efficient, returns smaller realization
```
