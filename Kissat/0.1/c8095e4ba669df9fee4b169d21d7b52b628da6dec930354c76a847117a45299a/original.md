new(clauses; max_var::Int = 0, configuration = nothing)::RawSolver

Creates a new solver, that self-destructs at end of life.

The optional arguments may specify a prereserved number max_var of literals, and a configuration in Set([:default, :sat, :plain, :basic, :unsat]).
