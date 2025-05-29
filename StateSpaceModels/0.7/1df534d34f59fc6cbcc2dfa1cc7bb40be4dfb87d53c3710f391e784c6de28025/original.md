```
SARIMA(
    y::Vector{Fl}; 
    order::Tuple{Int,Int,Int} = (1, 0, 0), 
    seasonal_order::Tuple{Int, Int, Int, Int} = (0, 0, 0, 0),
    include_mean::Bool = false,
    suppress_warns::Bool = false
) where Fl
```

A SARIMA model (Seasonal AutoRegressive Integrated Moving Average) implemented within the state-space framework.

The SARIMA model is specified $(p, d, q) \times (P, D, Q, s)$. We can also consider a polynomial $A(t)$ to  model a trend, here we only allow to add a constante term with the `include_mean` keyword argument.    

$$
\begin{gather*}
    \begin{aligned}
        \phi_p (L) \tilde \phi_P (L^s) \Delta^d \Delta_s^D y_t = A(t) + \theta_q (L) \tilde \theta_Q (L^s) \zeta_t
    \end{aligned}
\end{gather*}
$$

In terms of a univariate structural model, this can be represented as

$$
\begin{gather*}
    \begin{aligned}
    y_t & = u_t + \eta_t \\
    \phi_p (L) \tilde \phi_P (L^s) \Delta^d \Delta_s^D u_t & = A(t) + \theta_q (L) \tilde \theta_Q (L^s) \zeta_t
    \end{aligned}
\end{gather*}
$$

# Example

```jldoctest
julia> model = SARIMA(rand(100); order=(1,1,1), seasonal_order=(1,2,3,12))
SARIMA(1, 1, 1)x(1, 2, 3, 12) with zero mean
```

See more on [Airline passengers](@ref)

# References

  * Durbin, James, & Siem Jan Koopman. Time Series Analysis by State Space Methods: Second Edition.  Oxford University Press, 2012
