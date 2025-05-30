```
expinti(x::Real)
```

गणना करता है एक्स्पोनेंशियल इंटीग्रल फ़ंक्शन

$$
\operatorname{Ei}(x) = \int_{-\infty}^x \frac{e^t}{t} \mathrm{d}t,
$$

जो $-\Re[\operatorname{E}_1(-x)]$ के बराबर है जहाँ $\operatorname{E}_1$ `expint` फ़ंक्शन है।
