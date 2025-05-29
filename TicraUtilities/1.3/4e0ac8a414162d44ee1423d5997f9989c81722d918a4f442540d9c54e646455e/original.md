```
cut2 = convert_cut(cut::Cut, icomp::Integer)
```

Make a copy of `cut` and convert it to a new polarization basis determined by `icomp`.  Legal values  for `icomp` and their meanings:

  * 1 => Eθ and Eϕ
  * 2 => ERHCP and ELHCP
  * 3 => Eh and Ev (Ludwig 3 co and cx)
