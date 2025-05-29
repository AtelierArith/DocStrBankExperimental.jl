```
normalize(h::Hist1D; width=true)
```

Create a normalized histogram via division by `integral(h)`, when `width==true`, the resultant histogram has area under the curve equals 1.

!!! warning
    Implicit approximation is made when using `width=true` with histograms that have overflow bins: the overflow data lives inthe left/right most bins and the bin width is taken "as is".

