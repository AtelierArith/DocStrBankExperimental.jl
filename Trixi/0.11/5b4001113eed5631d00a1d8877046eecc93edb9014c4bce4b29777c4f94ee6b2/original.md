```
TrafficFlowLWREquations1D
```

The classic Lighthill-Witham Richards (LWR) model for 1D traffic flow. The car density is denoted by $u \in [0, 1]$ and  the maximum possible speed (e.g. due to speed limits) is $v_{\text{max}}$.

$$
\partial_t u + v_{\text{max}} \partial_1 [u (1 - u)] = 0
$$

For more details see e.g. Section 11.1 of 

  * Randall LeVeque (2002)

Finite Volume Methods for Hyperbolic Problems [DOI: 10.1017/CBO9780511791253](https://doi.org/10.1017/CBO9780511791253)
