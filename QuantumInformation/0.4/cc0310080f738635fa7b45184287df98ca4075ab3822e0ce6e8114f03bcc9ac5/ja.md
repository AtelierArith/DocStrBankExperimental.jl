```julia
werner_state(d, α)

```

  * `d`: ベクトルの長さ。
  * `α`: [0, 1] の範囲の実数。

返されるのは、$\frac{\alpha}{d}\left(\sum_{i=0}^{\sqrt{d}-1}|ii\rangle\right) \left(\sum_{i=0}^{\sqrt{d}-1}\langle ii|\right)+ \frac{1-\alpha}{d}\sum_{i=0}^{d-1}|i\rangle\langle i|$ で与えられる [Werner state](http://en.wikipedia.org/wiki/Werner_state) です。
