```
XPRS_TUNERTARGET
```

Tuner: Defines the tuner target – what should be evaluated when comparing two runs with different control settings. (integer)

Default value: `-1`

Values: -1 : Automatically determined. The tuner will choose the default target based on problem type. 0 : Solution time then gap. (MIP/MISLP default) 1 : Solution time then best bound. 2 : Solution time then best integer solution. 3 : The primal dual integral. 4 : Time only. (LP/SLP default) 5 : SLP objective only. (SLP/MISLP choice) 6 : SLP validation number only. (SLP/MISLP choice) 7 : Gap only. 8 : Best bound only. 9 : Best integer solution only. 10 : Best primal integral. (Only for individual instances, not for problem sets)
