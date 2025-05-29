```
samples = get_samples(seq::Sequence; off_val=0, max_rf_samples=Inf)
```

Returns the samples of the events in `seq`.

# Arguments

  * `seq`: (`::Sequence`) Sequence struct

# Keywords

  * `off_val`: (`::Number`, `=0`) offset value for amplitude. Typically used to hide points in   plots by setting it to `Inf`
  * `max_rf_samples`: (`::Integer`, `=Inf`) maximum number of samples for the RF struct

# Returns

  * `samples`: (`::NamedTuple`) contains samples for `gx`, `gy`, `gz`, `rf`, and `adc` events.   Each event, represented by `e::NamedTuple`, includes time samples (`e.t`) and amplitude   samples (`e.A`)
