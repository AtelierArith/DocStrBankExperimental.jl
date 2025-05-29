```
XPRS_CROSSOVEROPS
```

Newton barrier and hybrid gradient: a bit vector for adjusting the behavior of the crossover procedure. (integer)

Default value: `0`

Values are a bitset: bit 0 : Returned solution when the crossover terminates prematurely: 0: Return the last basis from the crossover; 1: Return the barrier solution. bit 1 : Select the crossover stages to be performed: 0: Perform both crossover stages; 1: Skip second crossover stage. bit 2 : Set crossover behaviour: 0: Force to perform all pivots; 1: Skip pivots that are numerically less reliable. bit 3 : Set crossover behaviour: 0: Perform standard crossover; 1: Perform a slower, but numerically more careful crossover.
