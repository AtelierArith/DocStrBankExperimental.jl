```
function LinkTensorsTTN(psi::TTN, M::CouplingModel)::LinkTensorsTTN
function LinkTensorsTTN(psi::TTN, optens::Vector{ITensor})::LinkTensorsTTN
function LinkTensorsTTN(psi::TTN, oppairs::Vector{Pair{String, Int}};
                        isfermions::Bool = true)::LinkTensorsTTN
```

Constructors for the `LinkTensorsTTN`.
