`DHChamber(;name, V₀, Eₘᵢₙ, n₁, n₂, τ, τ₁, τ₂, k, Eshift=0.0, inP=false)`

The Double Hill chamber/ventricle model is defined based on the vessel element, but has a time varying elastance function modelling the contraction of muscle fibres

The time varying elastance is calculated using the Double Hill model.

This model uses external helper functions `elastance` and `delastance` which describe the elastance function and the first derivative of it.

It calculates the elastance as:

E(t) = (Eₘₐₓ - Eₘᵢₙ) * e(t) + Eₘᵢₙ

where e(t) is the Double-Hill function.

Named parameters:

`V₀`:     stress-free volume (zero pressure volume)

`p₀`      pressure offset (defaults to zero)           this is present in some papers (e.g. Shi), so is           provided here for conformity. Defaults to 0.0

`Eₘᵢₙ`:   minimum elastance

`Eₘₐₓ`:   maximum elastance

`n₁`:     rise coefficient

`n₂`:     fall coefficient

`τ`:      pulse length [s]

`τ₁`:     rise timing parameter[s]

`τ₂`:     fall timimg paramter [s]

`k`:      elastance factor*

`Eshift`: time shift of contraction (for atria)

`inP`:    (Bool) formulate in dp/dt (default: false)

*Note: `k` is not an independent parameter, it is a scaling factor that corresponds to 1/max(e(t)), which ensures that e(t) varies between zero and 1.0, such that E(t) varies between Eₘᵢₙ and Eₘₐₓ.
