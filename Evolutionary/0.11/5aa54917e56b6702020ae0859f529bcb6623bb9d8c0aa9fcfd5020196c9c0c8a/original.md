```
sus(fitness, N)
```

Stochastic universal sampling (SUS) provides zero bias and minimum spread [^3]. SUS is a development of fitness proportionate selection (FPS). Using a comb-like ruler, SUS starts from a small random number, and chooses the next candidates from the rest of population remaining, not allowing the fittest members to saturate the candidate space. The individuals are mapped to contiguous segments of a line, such that each individual's segment is equal in size to its fitness exactly as in roulette-wheel selection. Here equally spaced pointers are placed over the line as many as there are individuals to be selected.

Consider $N$ the number of individuals to be selected, then the distance between the pointers are $1/N$ and the position of the first pointer is given by a randomly generated number in the range $[0, 1/N]$.

*Note*: Best used in maximization context.
