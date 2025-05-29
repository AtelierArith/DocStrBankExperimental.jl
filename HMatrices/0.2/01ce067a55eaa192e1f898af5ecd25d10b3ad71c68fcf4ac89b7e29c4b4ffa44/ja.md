```
HMatrix{T}(rowtree,coltree,adm)
```

`rowtree`と`coltree`を使用して、許容条件`adm`で空の`HMatrix`を構築します。この関数は階層行列の骨組みを構築しますが、**ブロック内の`data`フィールドは計算しません**。階層行列を組み立てるには、[`assemble_hmatrix`](@ref)を参照してください。
