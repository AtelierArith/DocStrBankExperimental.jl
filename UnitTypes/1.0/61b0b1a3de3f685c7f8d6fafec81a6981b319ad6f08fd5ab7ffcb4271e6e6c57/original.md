`macro u_str(unit::String)`

Macro to provide the 1.2u"cm" inline unit assignment.   `a = 1.2u"cm"`   This function relies on cm(1.2) existing as an alias for CentiMeter(1.2).

The macro works by converting the unit string into a function, which is called on (1) and returned.   This return is implicitly multiplied/concatenated with the rest of the source expression, calling the defined multiply method.
