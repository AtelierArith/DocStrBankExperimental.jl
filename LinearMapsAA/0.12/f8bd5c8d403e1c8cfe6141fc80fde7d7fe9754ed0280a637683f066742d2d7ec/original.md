```
B = LinearMapAO(A::LinearMapAX)
```

Make an AO from an AM, despite `idim` and `odim` being 1D, for expert users who want `B*X` to be an `Array`. Somewhat an opposite of `undim`.
