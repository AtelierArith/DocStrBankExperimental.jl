NEqProblem(residuals)   NEqProblem(residuals, options)

mathematical problem of finding zeros in the residual function of square systems of equations. The problem is defined by `residuals` which is an appropriate objective type (for example `NonDiffed`, `OnceDiffed`, ...) for the types of algorithm to be used.

Options are stored in `options` and are of the `NEqOptions` type. See more information about options using `?NEqOptions`.

The package NLSolversAD.jl adds automatic conversion of problems to match algorithms that require higher order derivates than provided by the user. It also adds AD constructors for a target number of derivatives.
