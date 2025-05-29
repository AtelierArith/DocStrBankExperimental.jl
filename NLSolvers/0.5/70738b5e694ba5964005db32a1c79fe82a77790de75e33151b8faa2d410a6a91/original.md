LeastSquaresProblem(residuals::VectorObjective)

A LeastSquaresProblem is used to represent the mathematical problem of finding the smallest possible sum of squared values of the elements of the residual function. The problem is defined by `residual` which is a `VectorObjective`.

Options are stored in `options` and are of the `NLsqOptions` type. See more information about options using `?NLsqOptions`.

The package NLSolversAD.jl adds automatic conversion of problems to match algorithms that require higher order derivates than provided by the user. It also adds AD constructors for a target number of derivatives.
