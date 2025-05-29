```
gaborkernel(;
    sqexponential_transform=IdentityTransform(), cosine_tranform=IdentityTransform()
)
```

Construct a Gabor kernel with transformations `sqexponential_transform` and `cosine_transform` of the inputs of the underlying squared exponential and cosine kernel, respectively.

# Definition

For inputs $x, x' \in \mathbb{R}^d$, the Gabor kernel with transformations $f$ and $g$ of the inputs to the squared exponential and cosine kernel, respectively, is defined as

$$
k(x, x'; f, g) = \exp\bigg(- \frac{\| f(x) - f(x')\|_2^2}{2}\bigg)
                 \cos\big(\pi \|g(x) - g(x')\|_2 \big).
$$
