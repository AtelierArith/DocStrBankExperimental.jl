Package: Smoothers

```
filter(b,a,x,si)
```

Apply a digital filter to x using the following linear, time-invariant difference equation

$$
y(n) = \sum_{k=0}^M d_{k+1} \cdot x_{n-k}-\sum_{k=1}^N c_{k+1} \cdot y_{n-k} 
\\ \forall n | 1\le n \le \left\| x \right\| | c=a/a_1, d=b/a_1
$$

The implementation follows the description of [Octave filter function](https://octave.sourceforge.io/octave/function/filter.html)

# Arguments

  * `a`: Vector of numerator coefficients for the filter rational transfer function.
  * `b`: Vector of denominator coefficients for the filter rational transfer function.
  * `x`: Vector of data.
  * `si`: Vector of initial states.

# Returns

Vector of filtered data

# Examples

```julia-repl
using Plots

t = Array(LinRange(-pi,pi,100));
x = sin.(t) .+ 0.25*rand(length(t));

# Moving Average Filter
w = 5; 
b = ones(w)/w;
a = [1];

plot(t,x,label="sin(x)",legend=:bottomright)
y1 = filter(b,a,x)
si = x[1:4] .+ .1;
y2 = filter(b,a,x,si)
plot!(t,y1,label="MA")
plot!(t,y2,label="MA with si")
```
