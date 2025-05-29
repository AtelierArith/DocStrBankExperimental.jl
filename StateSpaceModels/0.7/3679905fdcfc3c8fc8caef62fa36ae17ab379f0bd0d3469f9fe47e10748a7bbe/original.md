```
UnobservedComponents(
    y::Vector{Fl}; 
    X::Matrix{Fl} = zeros(Fl, length(y), 0),
    trend::String = "local level",
    seasonal::String = "no"
    cycle::String = "no"
) where Fl
```

An unobserved components model that can have trend/level, seasonal and cycle components.  Each component should be specified by strings, if the component is not desired in the model  a string with "no" can be passed as keyword argument. 

These models take the general form 

$$
\begin{gather*}
    \begin{aligned}
    y_t = \mu_t + \gamma_t + c_t + \varepsilon_t
    \end{aligned}
\end{gather*}
$$

where $y_t$ refers to the observation vector at time $t$, $\mu_t$ refers to the trend component, $\gamma_t$ refers to the seasonal component, $c_t$ refers to the cycle, and $\varepsilon_t$ is the irregular. The modeling details of these components are given below.

### **Trend**

The trend component can be modeled in a lot of different ways, usually it is called level when there is no slope component. The modelling options can be expressed as in the example `trend = "local level"`.

  * Local Level

string: `"local level"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad \varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \eta_{t} \quad \eta_{t} \sim \mathcal{N}(0, \sigma^2_{\eta})\\
    \end{aligned}
\end{gather*}
$$

  * Random Walk

string: `"random walk"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t}\\
        \mu_{t+1} &= \mu_{t} + \eta_{t} \quad \eta_{t} \sim \mathcal{N}(0, \sigma^2_{\eta})\\
    \end{aligned}
\end{gather*}
$$

  * Local Linear Trend

string: `"local linear trend"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \nu_{t} + \xi_{t} \quad &\xi_{t} \sim \mathcal{N}(0, \sigma^2_{\xi})\\
        \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \sigma^2_{\zeta})\\
    \end{aligned}
\end{gather*}
$$

  * Smooth Trend

string: `"smooth trend"`

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &=  \mu_{t} + \varepsilon_{t} \quad &\varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \mu_{t+1} &= \mu_{t} + \nu_{t}\\
        \nu_{t+1} &= \nu_{t} + \zeta_{t} \quad &\zeta_{t} \sim \mathcal{N}(0, \sigma^2_{\zeta})\\
    \end{aligned}
\end{gather*}
$$

**Seasonal**

The seasonal component is modeled as:

$$
\begin{gather*}
    \begin{aligned}
    \gamma_t = - \sum_{j=1}^{s-1} \gamma_{t+1-j} + \omega_t \quad \omega_t \sim N(0, \sigma^2_\omega)
    \end{aligned}
\end{gather*}
$$

The periodicity (number of seasons) is s, and the defining character is that (without the error term), the seasonal components sum to zero across one complete cycle. The inclusion of an error term allows the seasonal effects to vary over time. The modelling options can be expressed in terms of `"deterministic"` or `"stochastic"` and the periodicity as a number in  the string, i.e., `seasonal = "stochastic 12"`.

**Cycle**

The cycle component is modeled as

$$
\begin{gather*}
    \begin{aligned}
        c_{t+1} &= \rho_c \left(c_{t} \cos(\lambda_c) + c_{t}^{*} \sin(\lambda_c)\right) \quad & \tilde\omega_{t} \sim \mathcal{N}(0, \sigma^2_{\tilde\omega})\\
        c_{t+1}^{*} &= \rho_c \left(-c_{t} \sin(\lambda_c) + c_{t}^{*} \sin(\lambda_c)\right) \quad &\tilde\omega^*_{t} \sim \mathcal{N}(0, \sigma^2_{\tilde\omega})\\
    \end{aligned}
\end{gather*}
$$

The cyclical component is intended to capture cyclical effects at time frames much longer  than captured by the seasonal component. The parameter $\lambda_c$ is the frequency of the cycle and it is estimated via maximum likelihood. The inclusion of error terms allows the cycle effects to vary over time. The modelling options can be expressed in terms of `"deterministic"` or `"stochastic"` and the damping effect as a string, i.e.,  `cycle = "stochastic"`, `cycle = "deterministic"` or `cycle = "stochastic damped"`.

The UnobservedComponents model has some dedicated Plot Recipes, see [Visualization](@ref)

# References

  * Durbin, James, & Siem Jan Koopman. Time Series Analysis by State Space Methods: Second Edition.  Oxford University Press, 2012
