```
discriminant_group(L::ZZLat) -> TorQuadModule
```

`L`の判別群を返します。

整数格子`L`の判別群は、有限アーベル群`D = dual(L)/L`です。

それは判別双線形形式を備えています。

$$
D \times D \to \mathbb{Q} / \mathbb{Z} \qquad (x,y) \mapsto \Phi(x,y) + \mathbb{Z}.
$$

`L`が偶数である場合、判別群は判別二次形式$D \to \mathbb{Q} / 2 \mathbb{Z}, x \mapsto \Phi(x,x) + 2\mathbb{Z}$を備えています。
