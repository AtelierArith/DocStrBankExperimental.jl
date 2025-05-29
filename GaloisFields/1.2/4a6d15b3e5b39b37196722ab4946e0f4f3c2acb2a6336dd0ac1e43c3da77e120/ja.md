```
const G = @GaloisField! 3 β^2 + 1
const G = @GaloisField! 𝔽₃ β^2 + 1
const G = @GaloisField! 3^2 β
const K = GaloisField(3)
const G = @GaloisField! K β^2 + 1
```

有限体 `G` を定義し、その原始元の変数を現在のスコープに注入します。

変数名（上記の β など）は型の一部であることに注意してください。これにより、同型の（部分）体間の同定を定義できます。たとえば、次の定義を使用すると

```
const F = @GaloisField! 𝔽₂ β^2 + β + 1
const G = @GaloisField! 𝔽₂ γ^2 + γ + 1
```

体 $F$ と $G$ は同型ですが、標準的ではありません。次のように定義することができます。

```
@GaloisFields.identify β => γ + 1
@GaloisFields.identify γ => β + 1
```

これにより、次のような変換が可能になります。

```
G(β)
convert(F, γ + 1)
```
