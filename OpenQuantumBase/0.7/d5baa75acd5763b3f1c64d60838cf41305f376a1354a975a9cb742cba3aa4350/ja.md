```julia
DiffEqLiouvillian(
    H,
    opensys_eig,
    opensys,
    lvl;
    digits,
    sigdigits
)

```

`DiffEqLiouvillian`型のコンストラクタです。`opensys_eig`はハミルトニアンの対角化を必要とするオープンシステムリウビリアンのリストです。`opensys`はハミルトニアンの対角化を必要としないオープンシステムリウビリアンのリストです。`lvl`は、メソッドが切り捨てをサポートしている場合のエネルギー固有基底の切り捨てレベルです。
