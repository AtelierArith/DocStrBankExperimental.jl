```
struct RefDynamic <: TransmissionMode
```

A reference dynamic `TransmissionMode`.

Generic representation of dynamic transmission modes, using for example truck, ship or railway transport.

# Fields

  * **`id::String`** is the name/identifyer of the transmission mode.
  * **`resource::Resource`** is the resource that is transported.
  * **`trans_cap::TimeProfile`** is the capacity of the transmission mode.
  * **`trans_loss::TimeProfile`** is the loss of the transported resource during transmission, modelled as a ratio.
  * **`opex_var::TimeProfile`** is the variable operating expense per energy unit transported.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity.
  * **`directions`** is the number of directions the resource can be transported, 1 is unidirectional (A->B) or 2 is bidirectional (A<->B).
  * **`data::Vector{Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
