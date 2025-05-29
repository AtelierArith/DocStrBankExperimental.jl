A `FrequencyAdapter` adapts the frequencies with which a set of values/strategies/methods should be applied/tried in an optimization problem. It is based on the `Adaptive Coordinate Frequencies` scheme described in:

T. Glasmachers and U. Dogan, "Accelerated Coordinate Descent with Adaptive Coordinate Frequencies", 2013.

but generalized so that it can support more than the adaptation of only the coordinates in a Coordinate Descent scheme. The things that are being adapted are identified by integers in 1:n, with n being the main parameter.
