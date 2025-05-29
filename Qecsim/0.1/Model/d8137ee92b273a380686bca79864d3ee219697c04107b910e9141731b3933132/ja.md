```
validate(code)
```

整合チェックを実行します。

以下のいずれかが失敗した場合、[`QecsimError`](@ref) がスローされます：

  * $$
    S ⊙ S^T = 0
    $$
  * $$
    S ⊙ L^T = 0
    $$
  * $$
    L ⊙ L^T = Λ
    $$

ここで、$S$ と $L$ はそれぞれコードの [`stabilizers`](@ref) と [`logicals`](@ref) であり、$⊙$ と $Λ$ は [`PauliTools.bsp`](@ref bsp) で定義されています。
