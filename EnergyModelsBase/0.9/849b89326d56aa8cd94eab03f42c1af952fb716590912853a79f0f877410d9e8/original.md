```
scale_op_sp(t_inv::TS.AbstractStrategicPeriod, t::TS.TimePeriod)
```

Provides a simplified function for returning the multiplication

$duration(t) * multiple\_strat(t\_inv, t) * probability(t)$

when operational periods are coupled with strategic periods. It is used to scale the value provided for operational periods to a duration of 1 of a strategic period.

# Example

```julia
# Time structure representing to strategic periods with a duration of 4 years each and
# including a single week with hourly resolution
ts = TwoLevel(2, 4, SimpleTimes(168,1); op_per_strat=8760.0);

# Extracting the first strategic period and its first operational period
t_inv = first(strat_periods(ts))
t = first(t_inv)

# Calculating the value as 52.14 (number of weeks in a year)
scale_op_sp(t_inv, t)
```
