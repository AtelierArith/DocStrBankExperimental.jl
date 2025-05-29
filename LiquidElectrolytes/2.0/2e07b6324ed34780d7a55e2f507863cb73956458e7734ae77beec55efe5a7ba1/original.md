```
c0_barc(u,electrolyte)
```

Calculate solvent concentration $c_0$ and summary concentration $\bar c$ from vector of concentrations `c` using the incompressibility constraint (assuming $κ_0=0$):

$$
 \sum_{i=0}^N c_i (v_i + κ_iv_0) =1
$$

This gives

$$
 c_0v_0=1-\sum_{i=1}^N c_i (v_i+ κ_iv_0)
$$

$$
c_0= 1/v_0 - \sum_{i=1}^N c_i(\frac{v_i}{v_0}+κ_i)
$$

Then we can calculate 

$$
 \bar c= \sum_{i=0}^N c_i
$$
