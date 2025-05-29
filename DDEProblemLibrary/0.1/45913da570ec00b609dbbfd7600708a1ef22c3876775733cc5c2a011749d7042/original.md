```
prob_dde_DDETST_D2
```

Delay differential equation model of antigen antibody dynamics with fading memory, given by

$$
u_1'(t) = - r_1 u_1(t) u_2(t) + r_2 u_3(t), 
$$

$$
u_2'(t) = - r_1 u_1(t) u_2(t) + \alpha r_1 u_1(t - u_4(t)) u_2(t - u_4(t)),
$$

$$
u_3'(t) = r_1 u_1(t) u_2(t) - r_2 u_3(t), 
$$

$$
u_4'(t) = 1 + \frac{3 \delta - u_1(t) u_2(t) - u_3(t)}{u_1(t - u_4(t)) u_2(t - u_4(t)) + u_3(t - u_4(t))} \exp(\delta u_4(t)),
$$

for $t \in [0, 40]$ with history function

$$
\phi_1(t) = 5, 
$$

$$
\phi_2(t) = 0.1, 
$$

$$
\phi_3(t) = 0, 
$$

$$
\phi_4(t) = 0,
$$

for $t \leq 0$, where $r_1 = 0.02$, $r_2 = 0.005$, $\alpha = 3$, and $\delta = 0.01$.

# References

Gatica, J. and Waltman, P. (1982). A threshold model of antigen antibody dynamics with fading memory, in Lakshmikantham (ed.), Nonlinear phenomena in mathematical science, Academic Press, New York, pp. 425-439.
