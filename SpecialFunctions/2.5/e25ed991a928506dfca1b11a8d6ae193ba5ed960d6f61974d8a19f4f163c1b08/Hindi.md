```
ncbeta_tail(x,a,b,lambda)
```

गैरकेंद्रीय बीटा वितरण की पूंछ की गणना करें। पुनरावृत्त संबंध का उपयोग करता है

$$
I_{x}(a,b+1;0) = I_{x}(a,b;0) - \Gamma(a+b)/\Gamma(a+1)\Gamma(b) x^a (1-x)^b
$$

और $\Gamma(a+1) = a\Gamma(a)$ जो [DLMF 8.17.21](https://dlmf.nist.gov/8.17.21) में दिया गया है।
