```
minreal(sys::StateSpace; fast=false, balance=true, kwargs...)
```

P. Van Dooreenによる最小実現アルゴリズム、線形システム理論における一般化固有構造問題、IEEE Transactions on Automatic Control

オプションに関する情報は、`?ControlSystemsBase.MatrixPencils.lsminreal`を参照してください。

また、[`sminreal`](@ref)も参照してください。これは数値的に正確であり、`minreal`よりも大幅に高速ですが、非最小ダイナミクスを除去する可能性ははるかに限られています。
