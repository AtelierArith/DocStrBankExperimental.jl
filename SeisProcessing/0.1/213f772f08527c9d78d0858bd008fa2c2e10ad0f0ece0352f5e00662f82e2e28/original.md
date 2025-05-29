```
Ormsby(; <keyword arguments>)
```

Create a Ormsby wavelet sampled every dt seconds with corner frequencies defined by the vector f = [f1, f2, f3, f4]. The final wavelet is multiplied by a Hamming window.

# Arguments

  * `dt=0.002`: sampling interval in secs.
  * `f=[2.0, 10.0, 40.0, 60.0]`: corner frequencies in Hz.     ^   1 |     ***************     |    *               *     |   *                 *     |  *                   *     | *                     *     ––––––––––––––-> f       f1  f2           f3  f4

# Example

```julia
julia> w = Ormsby(); plot(w);
```
