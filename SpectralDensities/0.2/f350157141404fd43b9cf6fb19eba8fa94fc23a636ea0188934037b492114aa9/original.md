```
struct OhmicSD <: AbstractSD
```

OhmicSD represents an Ohmic spectral density. It is characterized by an amplitude `α` representing the strength of the Ohmic coupling. That is

$$
J(\omega) = \alpha\omega
$$

# Fields

  * `α::Float64`: The amplitude `α`, indicating the strength of the Ohmic coupling.
