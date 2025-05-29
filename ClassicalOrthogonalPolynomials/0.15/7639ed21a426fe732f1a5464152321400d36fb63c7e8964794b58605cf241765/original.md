ChebyshevWeight{kind,T}()

is a quasi-vector representing the Chebyshev weight of the specified kind on -1..1. That is, `ChebyshevWeight{1}()` represents `1/sqrt(1-x^2)`, and `ChebyshevWeight{2}()` represents `sqrt(1-x^2)`.
