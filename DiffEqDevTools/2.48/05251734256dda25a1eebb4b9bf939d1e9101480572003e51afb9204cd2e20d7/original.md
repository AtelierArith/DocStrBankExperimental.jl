`appxtrue(sol::AbstractODESolution,sol2::AbstractODESolution)`

Uses the interpolant from the higher order solution sol2 to approximate errors for sol. If sol2 has no interpolant, only the final error is calculated.
