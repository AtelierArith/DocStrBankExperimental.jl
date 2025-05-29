The LPAC Cold-Start AC Power Flow Approximation.

Note that the LPAC Cold-Start model requires the least amount of information but is also the least accurate variant of the LPAC Models.  If a nominal AC operating point is available, the LPAC Warm-Start model will provide improved accuracy.

The original publication suggests to use polyhedral outer approximations for the cosine and line thermal lit constraints.  Given the recent improvements in MIQCQP solvers, this implementation uses quadratic functions for those constraints.

```
@article{doi:10.1287/ijoc.2014.0594,
  author = {Coffrin, Carleton and Van Hentenryck, Pascal},
  title = {A Linear-Programming Approximation of AC Power Flows},
  journal = {INFORMS Journal on Computing},
  volume = {26},
  number = {4},
  pages = {718-734},
  year = {2014},
  doi = {10.1287/ijoc.2014.0594},
  eprint = {https://doi.org/10.1287/ijoc.2014.0594}
}
```
