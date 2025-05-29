```
discriminant_group(L::ZZLat) -> TorQuadModule
```

Return the discriminant group of `L`.

The discriminant group of an integral lattice `L` is the finite abelian group `D = dual(L)/L`.

It comes equipped with the discriminant bilinear form

$$
D \times D \to \mathbb{Q} / \mathbb{Z} \qquad (x,y) \mapsto \Phi(x,y) + \mathbb{Z}.
$$

If `L` is even, then the discriminant group is equipped with the discriminant quadratic form $D \to \mathbb{Q} / 2 \mathbb{Z}, x \mapsto \Phi(x,x) + 2\mathbb{Z}$.
