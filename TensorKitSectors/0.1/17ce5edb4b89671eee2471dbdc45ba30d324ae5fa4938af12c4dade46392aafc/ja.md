```
struct SU2Irrep <: AbstractIrrep{SU₂}
SU2Irrep(j::Real)
Irrep[SU₂](j::Real)
```

$$
SU₂
$$

の群の不変表現を表します。不変表現は、任意の実数として入力できる半整数 `j` によってラベル付けされますが、HalfIntegers.jl パッケージの `HalfInt` として保存されます。

## フィールド

  * `j::HalfInt`: 不変表現のラベルで、任意の非負半整数を指定できます。
