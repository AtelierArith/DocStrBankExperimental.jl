```
ncbeta_poisson(a,b,lambda,x)
```

यदि `lambda >= 54` है तो गैर-केंद्रीय बीटा का CDF निकालें: पहले $\lambda/2$ की गणना की जाती है और पॉइसन पद की गणना $P(j-1) = j/\lambda P(j)$ और $P(j+1) = \lambda/(j+1) P(j)$ का उपयोग करके की जाती है। फिर पीछे की पुनरावृत्तियों का उपयोग किया जाता है जब तक कि या तो पॉइसन भार `errmax` से नीचे नहीं गिरते या `iterlo` तक नहीं पहुँचते।

$$
I_{x}(a+j-1,b) = I_{x}(a+j,b) + \Gamma(a+b+j-1)/\Gamma(a+j)\Gamma(b)x^{a+j-1}(1-x)^{b}
$$

फिर आगे की पुनरावृत्तियों का उपयोग किया जाता है जब तक कि त्रुटि सीमा `errmax` से नीचे नहीं गिरती।

$$
I_{x}(a+j+1,b) = I_{x}(a+j,b) - \Gamma(a+b+j)/\Gamma(a+j)\Gamma(b)x^{a+j}(1-x)^{b}
$$
