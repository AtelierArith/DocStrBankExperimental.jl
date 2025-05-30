```
beta_inc_cont_fraction(a,b,x,y,lambda,epps)
```

जब `a, b > 1` हो, तब निरंतर भिन्न विस्तार का उपयोग करके $I_{x}(a,b)$ की गणना करें। यह माना गया है कि $\lambda = (a+b)*y - b$

बाहरी लिंक: [DLMF 8.17.22](https://dlmf.nist.gov/8.17.22), [विकिपीडिया](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

देखें: [`beta_inc`](@ref)

# कार्यान्वयन

`BFRAC(A,B,X,Y,LAMBDA,EPS)` [Didonato और Morris (1992)](@cite didonato_1992) से
