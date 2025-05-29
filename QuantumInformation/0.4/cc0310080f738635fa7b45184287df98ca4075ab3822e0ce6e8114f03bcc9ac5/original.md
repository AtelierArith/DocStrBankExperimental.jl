```julia
werner_state(d, α)

```

  * `d`: length of the vector.
  * `α`: real number from [0, 1].

Returns [Werner state](http://en.wikipedia.org/wiki/Werner_state) given by $\frac{\alpha}{d}\left(\sum_{i=0}^{\sqrt{d}-1}|ii\rangle\right) \left(\sum_{i=0}^{\sqrt{d}-1}\langle ii|\right)+ \frac{1-\alpha}{d}\sum_{i=0}^{d-1}|i\rangle\langle i|$.
