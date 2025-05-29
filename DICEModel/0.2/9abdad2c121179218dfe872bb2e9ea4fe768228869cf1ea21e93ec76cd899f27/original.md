```
run_dice_scenario(scenario::String)
```

Run one of the "official" 11 scenarios in Nordhous's DICE 2023 model:

  * `cbopt`: The C/B optimal scenario
  * `t2c`:   The temperature constrained to max 2 °C scenario
  * `t15c`:   The temperature constrained to max 1.5 °C scenario
  * `altdam`: The alternative damage scenario
  * `parisext`: The Paris extended scenario
  * `base`:     The base (current policies) scenario
  * `r5`:       The scenario with discount rate of 5%
  * `r4`:       The scenario with discount rate of 4%
  * `r3`:       The scenario with discount rate of 3%
  * `r2`:       The scenario with discount rate of 2%
  * `r1`:       The scenario with discount rate of 1%

To run "your own" scenarios, use the function [`run_dice`](@ref), where you can set the input parameters and constraints as you like.

# Output

  * A named tuple containing the following fields: `solved`, `status`, `times`, `tidx`, the post_process computed values and the optimization variables.
