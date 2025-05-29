```
@enumx PhysicalScale
```

EnumX instance representing the physical scale of a reaction. 

Notes: The following values are possible:

  * `Auto`: (DEFAULT) Lets Catalyst decide at the time of system conversion and/or problem generation at what physical scale to represent the reaction.
  * `ODE`: The reaction is to be treated via an ordinary differential equation term.
  * `SDE`: The reaction is to be treated via a stochastic differential equation (CLE) term.
  * `Jump`: The reaction is to be treated via a jump process (stochastic chemical kinetics) term, letting Catalyst decide the specific jump type.
  * `VariableRateJump`: The reaction is to be treated as a jump process (stochastic chemical kinetics) term, specifically assigning it to a VariableRateJump.
