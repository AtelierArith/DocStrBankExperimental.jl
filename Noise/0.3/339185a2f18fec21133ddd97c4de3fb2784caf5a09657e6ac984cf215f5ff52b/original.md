```
salt_pepper(X; salt_prob=0.5, salt=1.0, pepper=0.0[, prob=0.1])
```

Returns array `X` affected by salt and pepper noise. `X` can be an array or an RGB or Gray image `prob` is a optional argument for the probability that a pixel will be affected by the noise. `salt_prob` is a keyword argument representing the probability for salt noise.  The probability for pepper noise is therefore 1-`salt_prob`. `salt` is a keyword argument for specifying the value of salt noise. `pepper` is a keyword argument for specifying the value of pepper noise.
