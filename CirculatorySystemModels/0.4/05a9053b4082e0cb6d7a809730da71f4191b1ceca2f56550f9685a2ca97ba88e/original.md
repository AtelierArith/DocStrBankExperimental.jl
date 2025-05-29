`VariableElastance(; name, V₀=0.0, C=1.0, Escale=1.0, fun, inP=false, has_ep=false, has_variable_ep=false, p₀=0.0)`

`VariableElastance` is defined based on the `Elastance` element, but has a time varying elastance function modelling the contraction of muscle fibres.

Named parameters:

`V₀`:              stress-free volume (zero pressure volume)

`Escale`:          scaling factor (elastance factor)

`fun`:             function object for elastance (must be `fun(t)`)

`inP`:             (Bool) formulate in dp/dt (default: false)

`has_ep`:          (Bool) if true, add a parameter `p₀` for pressure offset                    e.g., for thoracic pressure (default: false)

`p₀`:              External pressure in mmHg (e.g., thorax pressure, default: 0.0)                    *Note: if this argument is set, it will be used, even if `has*ep`is`false`.`has*ep`only controls if`p₀` will be exposed as a parameter!*

has*variable*ep`: (Bool) expose pin for variable external pressure (default: false)                    This pin can be connected to another pin or function providing external pressure.                    _Note: if`has*variable*ep`is set to`true`this pin is created, independent of`has*ep`!*
