```
discrete_observation_times(Q, k=2^10, t=0.0)
```

Approximate 𝐑(t) = exp(t𝐐) using P₄ of Yoon & Shanthikumar (1989, p. 181), where the Rᵢⱼ are the probability of starting at state 𝑗 and ending at state 𝑖 at time 𝑡. The k parameter should be set to a power of two for efficiency.

This method can give inaccurate results if k ≤ t * getmaxrate(Q)!
