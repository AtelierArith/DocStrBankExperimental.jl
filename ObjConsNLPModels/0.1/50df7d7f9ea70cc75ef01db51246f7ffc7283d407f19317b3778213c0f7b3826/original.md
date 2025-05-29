Implement an `AbstractNLPModel` that provides objective, constraint, and their first derivatives.

The single exported function is [`objcons_nlpmodel`](@ref).

# Motivation

Consider a problem

$$
\min_x f(g(x)) \text{ subject to } h(g(x)) == 0
$$

where `g` is an expensive function. A typical example is structural estimation in macroeconomics, where `g` would calculate something expensive like mass distributions, `f` the moments and `h` the equilibrium conditions. The implementation allows the user to define these in one step.
