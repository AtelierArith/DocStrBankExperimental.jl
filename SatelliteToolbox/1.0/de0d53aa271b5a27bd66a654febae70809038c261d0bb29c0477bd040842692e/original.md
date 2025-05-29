```
equation_of_time(t::Union{Number, DateTime})
```

Compute the difference between the Sun apparent local time and the Sun mean local time [rad], which is called Equation of Time, at the time `t`, which can be represented by a Julian Day or `DateTime`. The algorithm was adapted from **[1, p. 178, 277-279]**.

# References

  * **[1]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. 4th ed.   Microcosm Press, Hawthorne, CA.
