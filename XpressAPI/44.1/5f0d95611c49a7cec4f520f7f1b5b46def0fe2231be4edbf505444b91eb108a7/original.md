```
XPRS_BARCRASH
```

Newton barrier and hybrid gradient: This determines the type of crash used for the crossover. (integer)

During the crash procedure, an initial basis is determined which attempts to speed up the crossover. A good choice at this stage will significantly reduce the number of iterations required to crossover to an optimal solution. The possible values increase proportionally to their time-consumption.

Default value: `4`

Values: 0 : Turns off all crash procedures. 1-6 : Available strategies with 1 being conservative and 6 being aggressive.
