```
struct MDEIMReduction{A,R<:Reduction{A,EuclideanNorm}} <: AbstractMDEIMReduction{A}
  reduction::R
end
```

MDEIM struct employed in steady problems
