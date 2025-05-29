A solver backend that casts the (potentially nonlinear and non-convex) trajectory optimization problem as a mixed complementarity problem (MCP) and solves it via PATH.

The MCP is drived from the KKT conditions of the problem and takes the form

find   z s.t.   lᵢ == zᵢ       Fᵢ(z) >= 0        lᵢ <  zᵢ <  u, Fᵢ(z) == 0              zᵢ == u, Fᵢ(z) <= 0

# Note

The PATH solver is not open source but provides a free license. Without setting a license key, this backend only works for small problems. Please consult the documentation of [PATHSolver.jl](https://github.com/chkwon/PATHSolver.jl) to learn about loading the license key.
