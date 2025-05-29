AbstractControlParameter provides a unified interface to represent a control parameter for a polymer system. The control parameter can be varied to change the properties of a polymer system.

Concrete types include:

  * ϕControlParameter
  * αControlParameter
  * fControlParameter
  * χNControlParameter
  * bControlParameter

The functor of each concrete type will return either a list or a scalar values of the parameters which fully detemines its setting.
