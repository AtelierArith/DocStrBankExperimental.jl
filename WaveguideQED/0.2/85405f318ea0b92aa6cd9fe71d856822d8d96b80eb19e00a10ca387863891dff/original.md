```
expect_waveguide(O, psi,buffer)
```

Returns the sum of expectation values of O over waveguide time indeces. This is usefull to extract information from waveguide states. For example the number of photons can be computed as: `expect_waveguide(create(bw)*destroy(bw), psi, times)`, where BW is the waveguidebasis. Mathematically this is equivalent to $sum_n \langle \psi | O(t_n) | \psi \rangle$. For $O(t_k) = w_k^\dagger w_k$ acting on a single photon state $|\psi \rangle = \sum_k \xi(t_k) w_k^\dagger |0\rangle$, one would therefore have: $\langle O \rangle = \sum_k |\xi(t_k)|^2 = 1$, where the last follows from $\xi(t)$ being normalized.
