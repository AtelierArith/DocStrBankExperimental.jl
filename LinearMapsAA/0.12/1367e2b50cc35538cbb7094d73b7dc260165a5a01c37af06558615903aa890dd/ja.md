```
 mul!(yv, AO::LinearMapAO, xv, α, β)
```

`yv` と `xv` がそれぞれ AbstractArrays の `Vector` であるときのファンシーな 5 引数の乗算。基本的には `mul!(yv[i], A, xv[i], α, β)` を `i in 1:length(xv)` に対して行います。
