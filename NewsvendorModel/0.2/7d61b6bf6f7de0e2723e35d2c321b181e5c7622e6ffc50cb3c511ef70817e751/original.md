```
q_opt(anp::AbstractNewsvendorProblem; rounded = true)
```

Compute the quanitity that maximizes expected profit for a newsvendor problem (i.e., where critical fractile equals in-stock probability). Attempts to solve 

$$
F(q_{opt}) = \textrm{critical fractile} 
$$

where F is the c.d.f. of the demand distribution. Returns closest next integer unless `rounded=false`; then, it returns exact real. Clamps at q*min and q*max.
