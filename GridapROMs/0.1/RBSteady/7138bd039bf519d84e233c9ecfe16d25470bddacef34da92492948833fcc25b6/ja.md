```
struct MDEIMReduction{A,R<:Reduction{A,EuclideanNorm}} <: AbstractMDEIMReduction{A}
  reduction::R
end
```

定常問題に使用されるMDEIM構造体
