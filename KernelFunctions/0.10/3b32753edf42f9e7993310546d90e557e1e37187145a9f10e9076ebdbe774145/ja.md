```
gaborkernel(;
    sqexponential_transform=IdentityTransform(), cosine_tranform=IdentityTransform()
)
```

入力の基になる二乗指数およびコサインカーネルの変換 `sqexponential_transform` と `cosine_transform` を用いてガボールカーネルを構築します。

# 定義

入力 $x, x' \in \mathbb{R}^d$ に対して、二乗指数およびコサインカーネルへの入力の変換 $f$ と $g$ を持つガボールカーネルは次のように定義されます。

$$
k(x, x'; f, g) = \exp\bigg(- \frac{\| f(x) - f(x')\|_2^2}{2}\bigg)
                 \cos\big(\pi \|g(x) - g(x')\|_2 \big).
$$
