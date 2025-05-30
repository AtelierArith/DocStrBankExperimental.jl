```
ncbeta_poisson(a,b,lambda,x)
```

非中心ベータのCDFを計算します。`lambda >= 54` の場合、まず $\lambda/2$ を計算し、ポアソン項は $P(j-1) = j/\lambda P(j)$ および $P(j+1) = \lambda/(j+1) P(j)$ を使用して計算されます。次に、ポアソン重みが `errmax` を下回るか、`iterlo` に達するまで後方再帰が使用されます。

$$
I_{x}(a+j-1,b) = I_{x}(a+j,b) + \Gamma(a+b+j-1)/\Gamma(a+j)\Gamma(b)x^{a+j-1}(1-x)^{b}
$$

その後、誤差境界が `errmax` を下回るまで前方再帰が使用されます。

$$
I_{x}(a+j+1,b) = I_{x}(a+j,b) - \Gamma(a+b+j)/\Gamma(a+j)\Gamma(b)x^{a+j}(1-x)^{b}
$$
