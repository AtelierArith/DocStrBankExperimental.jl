```
beta_inc_asymptotic_symmetric(a,b,lambda,epps)
```

$$
I_{x}(a,b)
$$

की गणना करें असिम्प्टोटिक विस्तार का उपयोग करते हुए `a, b >= 15` के लिए। यह माना गया है कि $\lambda = (a+b)*y - b$।

बाहरी लिंक: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

देखें: [`beta_inc`](@ref)

# कार्यान्वयन

`BASYM(A,B,LAMBDA,EPS)` [Didonato और Morris (1992)](@cite didonato_1992) से
