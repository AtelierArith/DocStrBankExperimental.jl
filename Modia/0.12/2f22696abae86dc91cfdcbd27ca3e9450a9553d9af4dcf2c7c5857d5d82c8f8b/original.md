```
(success, AST, equationInfo) = getSortedAndSolvedAST(
                                    G, BLT, assign, A, B, stateSelectionFunctions;
                                    log = false, logDetails=false, modelName = "???",
                                    defaultParameterAndStartValues = nothing,
                                    unitless=false)
```

From the BLT on highest derivative level `(G, BLT, assign, A, B)`, a set of callback functions `stateSelectionFunctions`, this function returns the AST (Abstract Syntax Tree) of the sorted and solved equations as a vector of `Expr` and information about the ODE equations (especially names of the ODE states).

# Input arguments

  * `G`: G[i] is the Integer vector of variable indices of equation i.  A variable i can be a scalar or an array.  is of type Vector{ Vector{Int} } or Vector{ Any }.
  * `BLT::Vector{Vector{Int}}`: BLT[i] is the vector of equations belonging to BLT-block i. In principal, **BLT[i] must include only highest derivative equations**. In order to ease the generation of BLT[i], to not be forced to map indices forth and back when calling the function that computes the BLT, the following assumption is made: If BLT[j] contains only **one equation with B[j][1] > 0** then this BLT block is a lower-derivative (dummy) block and is ignored.
  * `assign::Vector{Int}`: ei = assign[vi] is equation ei assigned to variable vi
  * `A`: A-Vector of Pantelides algorithm:      `A[i] = if der(v[i]) == v[k] then k else 0`      where `v[i]` is variable `i`.
  * `B`: B-Vector of Pantelides algorithm:      `B[i] = if der(e[i]) == e[k] then k else 0`      where `e[i]` is equation `i`.
  * `stateSelectionFunctions`: An instance of immutable struct [`StateSelectionFunctions`](@ref) that holds the information about the callback functions needed by `getSortedAndSolvedAST`.
  * `log`: = true: Print debug information (to find bugs in the code).
  * `logDetails`: = true: Print detailed debug information, if `log = true`.
  * `modelName`: Name of model used in messages (otherwise not used).

# Output arguments

A tuple with the following values:

  * `success::Bool`: = true, if generation was successful. = false, if an error occured. Arguments `AST, equationInfo` hold the information that have been collected until the error was detected.
  * `AST::Vector{Expr}`: The AST (Abstract Syntax Tree) of the sorted and solved equations as Vector of `Expr`.
  * `equationInfo::`[`Modia.EquationInfo`](@ref): Object that defines the states of the ODE.

When variable `v` has neither a `start` nor `init` attribute defined, it is assumed to have `start=0.0`.

| defined | Description                                               |
|:------- |:--------------------------------------------------------- |
| `start` | `start` is allowed to be changed during initialization    |
| `init`  | `init` is not allowed to be changed during initialization |

Note, `start, init` influence the state selection.

If an ODE state has neither a `start` nor an `init` value defined, a warning message is printed (start/init value missing).

If a solved variable has an `init` value, an information message is printed in case `log=true` (init value has no effect).

# Sketch of the Algorithm

Note, a statement *error xxx* means that an error occurs, because it is not possible to transform the equations to an ODE.

## Generate equation sets

From BLT blocks that are not further differentiated (= highest order BLT blocks), generate the equation sets as described by the dummy derivative method of [Mattsson and Söderlind (1992)](https://ieeexplore.ieee.org/document/274429). See also sections 4.5 and 4.6 of the paper [Otter and Elmqvist (2017)](https://modelica.org/events/modelica2017/proceedings/html/submissions/ecp17132565_OtterElmqvist.pdf).

## Define initial ODE states

Initially, all differentiated variables are defined to be ODE states. Whenever an initial ODE state is explicitly solved for in the course of the algorithm, the variable is no longer an ODE state.

## Analyse equation sets

For every equation set on every differentiation level perform the following actions:

  * If the equation set consists of *one* equation in *one* unknown, the equation is solved for this unknown (*error, if this is not possible*).
  * If the equation set consists of *N linear* equations in *N* unknowns solve this equation system (*error, if no linear system*):
    The equations are first teared to reduce the number of iteration variables and afterwards the teared equation system is solved with a special iterator loop that solves a linear equation system with an LU decomposition with column pivoting (for details see [`Modia.LinearEquationsIteration!`](@ref)).
  * If the equation set consists of *N linear* equations in *M* unknowns (*M > N*) perform the following actions (*error, if no linear system*).
    Note, due to the structure of BLT, this equation set cannot be on highest derivative level; due to the Pantelides algorithm, M < N is not possible).

    1. Solve the equation system explicitly via tearing for N unknowns (*error, if this is not possible*). Use start/init attributes of the M unknowns to influence tearing (e.g. it is tried to eliminate first variables that have neither start not init values).
    2. The N solved variables have been initially ODE states and are now defined to be no ODE states (so called dummy states, that is algebraic variables).

A BLT transformation of **all equations** is made under the assumption that the selected ODE states are known. This phase is needed, because the dummy-derivative ordering at the beginning does not necessarily provide already the right ordering. In this phase the information from the previous phase is used (that is the already determined tearing variables for systems of equations are utilized).
