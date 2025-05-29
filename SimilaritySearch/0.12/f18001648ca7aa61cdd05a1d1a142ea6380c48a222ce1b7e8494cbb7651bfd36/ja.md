```
macrorecall(goldI::AbstractMatrix, resI::AbstractMatrix, k=size(goldI, 1))::Float64
```

goldIをゴールドスタンダード、resIを予測として使用してマクロリコールスコアを計算します。整数（識別子）の行列を期待します。`k`が指定されている場合、結果は最初の`k`に切り捨てられます。
