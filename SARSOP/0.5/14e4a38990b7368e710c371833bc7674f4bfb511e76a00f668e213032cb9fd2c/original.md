```
SARSOPEvaluator
```

simulate a sarsop policy from the xml files 

  * `sim_len`  number of steps to use in simulation (default 10)
  * `sim_num` number of simulations
  * `fast` use fast (but very picky) alternate parser for .pomdp files
  * `srand` set the random seed for the simulation
  * `memory` [MB] No memory limit by default. If memory usage exceeds the specified value, the evaluator will switch back

to a more conservative (and slow) methods.

  * `output_file` where to write the results
  * `policy_filename` policy file location
  * `pomdp_filename` pomdpx file location
