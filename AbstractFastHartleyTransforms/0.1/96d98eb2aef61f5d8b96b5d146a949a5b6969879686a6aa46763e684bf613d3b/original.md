```
ifft(A [, dims])
```

Multidimensional inverse FHT.

A one-dimensional inverse FHT computes the one-dimensional inverse DHT (IDHT) defined by as

$$
\operatorname{IDHT}(A)[k] = \frac{1}{\operatorname{length}(A)} \operatorname{DHT}(A)[k]
$$

A multidimensional inverse FHT simply performs this operation along each transformed dimension of `A`.
