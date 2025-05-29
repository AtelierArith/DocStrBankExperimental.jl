```
erlangization(Q, k=2^10, t=0.0)
```

Approximate 𝐑(t) = exp(t𝐐) using P₃ of Yoon & Shanthikumar (1989, p. 179), originally from Ross (1987), where the Rᵢⱼ are the probability of starting at state 𝑗 and ending at state 𝑖 at time 𝑡. The k parameter should be set to a power of two for efficiency.
