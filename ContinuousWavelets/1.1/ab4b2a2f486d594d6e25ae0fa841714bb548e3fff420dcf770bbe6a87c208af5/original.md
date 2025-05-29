```
father(c::CWT, ω, averagingType::aT) where {aT<:Averaging}
```

This creates the averaging function, which covers the low frequency information, and is emphatically not analytic. `aT` determines whether it has the same form as the wavelets (`Father`), or just a bandpass `Dirac`. `c.averagingLength` gives the number of octaves (base 2) that are covered by the averaging function. The width is then derived so that it matches the next wavelet at 1σ.

For the Morlet wavelet, the distribution is just a Gaussian, so it has variance 1/s^2 and mean σ[1]*s set the variance so that the averaging function has σ/2 at the central frequency of the last scale.

For the Paul wavelets, it's a easy calculation to see that the mean of a paul wavelet of order m is (m+1)/s, while σ=sqrt(m+1)/s. So we set the variance so that the averaging function has 1σ at the central frequency of the last scale.

The derivative of a Gaussian (Dog) has a pretty nasty form for the mean and variance; eventually, if you set 1/2 * σ*{averaging}=⟨ω⟩*{highest scale wavelet}, you will get the scale of the averaging function to be `s*gamma((c.α+2)/2)/sqrt(gamma((c.α+1)/2)*(gamma((c.α+3)/2)-gamma((c.α+2)/2)))`
