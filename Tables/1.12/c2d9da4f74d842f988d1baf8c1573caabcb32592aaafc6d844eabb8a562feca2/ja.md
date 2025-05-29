```
Tables.table(m::AbstractVecOrMat; [header])
```

`AbstractVecOrMat`（`Matrix`、`Vector`、`Adjoint`など）を `MatrixTable` にラップし、Tables.jl インターフェースを満たします。 （`AbstractVector` は 1 列の行列として扱われます。）これにより、`Tables.rows` および `Tables.columns` を介して行列にアクセスできます。オプションのキーワード引数イテレータ `header` を渡すことができ、これは列名として使用される `Vector{Symbol}` に変換されます。`AbstractVecOrMat` のコピーは作成されないことに注意してください。
