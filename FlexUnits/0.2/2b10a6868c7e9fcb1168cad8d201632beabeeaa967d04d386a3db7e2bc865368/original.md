An abstract object representing a unit transformation formula.  Any object that subtypes this is made callable.

# Callable form

utrans = uconvert(u"°C", u"°F") utrans(0.0) 31.999999999999986

# Shorthand callable form (syntactic sugar)

(u"°C" |> u"°F")(0.0) 31.999999999999986
