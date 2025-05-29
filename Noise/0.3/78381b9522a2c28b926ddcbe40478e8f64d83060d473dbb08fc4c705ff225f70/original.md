```
salt_pepper_chn(X; salt_prob=0.5, salt=1.0, pepper=0.0[, prob=0.1])
```

Returns a RGB Image `X` affected by salt and pepper noise. When a salt or pepper occurs, it is applied to all channels of the RGB making a real salt and pepper on the whole image. `prob` is a optional argument for the probability that a pixel will be affected by the noise. `salt_prob` is a keyword argument representing the probability for salt noise.  The probability for pepper noise is therefore 1-`salt_prob`. `salt` is a keyword argument for specifying the value of salt noise. `pepper` is a keyword argument for specifying the value of pepper noise.
