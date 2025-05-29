```
@ForwardDiff_frule signature mutating
```

`mutating`は、関数が入力引数を変更しているかどうかを示します。

# 例

`LinearAlgebra.exp!`のルールを定義するには、これは変更を行う関数であるため、マクロを次のように呼び出します。

```julia
@ForwardDiff_frule LinearAlgebra.exp!(A::AbstractMatrix{<:ForwardDiff.Dual}) true
```
