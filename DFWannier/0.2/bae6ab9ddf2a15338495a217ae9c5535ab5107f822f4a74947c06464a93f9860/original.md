```
read_spn(filename)
```

Reads a .spn file and returns the DFT Sx, Sy, Sz. They are a `Vectors` with **nk** `Matrices` of size (**nb**, **nb**), where **nk** is the number of *k*-points and **nb** the number of bands.
