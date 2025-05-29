```
p4est_connectivity_new_icosahedron()
```

Create a connectivity for mapping the sphere using an icosahedron.

The regular icosadron is a polyhedron with 20 faces, each of which is an equilateral triangle. To build the `p4est` connectivity, we group faces 2 by 2 to from 10 quadrangles, and thus 10 trees.

This connectivity is meant to be used together with p4est*geometry*new_icosahedron to map the sphere.

The flat connectivity looks like that: Vextex numbering:

A00 A01 A02 A03 A04 / \ / \ / \ / \ / \ A05–-A06–-A07–-A08–-A09–-A10 \ / \ / \ / \ / \ / \ A11–-A12–-A13–-A14–-A15–-A16 \ / \ / \ / \ / \ / A17 A18 A19 A20 A21

Origin in A05.

Tree numbering:

0 2 4 6 8 1 3 5 7 9

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_new_icosahedron ();
```
