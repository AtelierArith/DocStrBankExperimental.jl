```
FIRFilter(h, rate[, Nϕ])
```

Returns a polyphase FIRFilter object from the vector of filter taps `h`. `rate` is a floating point number that specifies the input to output sample-rate relationship $\frac{fs_{out}}{fs_{in}}$. `Nϕ` is an optional parameter which specifies the number of *phases* created from `h`. `Nϕ` defaults to 32.
