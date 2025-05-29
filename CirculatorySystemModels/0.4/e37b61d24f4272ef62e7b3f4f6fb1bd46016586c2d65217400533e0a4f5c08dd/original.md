`ShiChamber(;name, V₀, p₀=0.0, Eₘᵢₙ, Eₘₐₓ, τ, τₑₛ, τₑₚ, Eshift=0.0)`

Implemention of a ventricle following Shi/Korakianitis.

This model uses external helper function `shiElastance` which describes the elastance function.

Named parameters:

`V₀`     stress-free volume (zero pressure volume)

`p₀`     pressure offset (defaults to zero)          this is present in the original paper, so is          provided here for conformity. Defaults to 0.0

`Eₘᵢₙ`   minimum elastance

`τ`      pulse length

`τₑₛ`    end systolic time (end of rising cosine)

`τₑₚ`    end pulse time (end of falling cosine)

`Eshift`: time shift of contraction (for atria), set to `0` for ventricle

`inP`:    (Bool) formulate in dp/dt (default: false)
