```
Centered()
```

中心を指定することで、その軸に沿って自動的に次元を中心に配置します。

例:

```julia
cube = load("abc.fits", (X=Centered(), Y=Centered(), Pol=[:I, :Q, :U]))
```

この場合、cubeはX軸とY軸の両方で画像の中心が0になる次元を持ちます。
