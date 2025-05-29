```
error_contract(y::MPS, A::MPO, x::MPS;
               make_inds_match::Bool = true)
error_contract(y::MPS, x::MPS, A::MPO;
               make_inds_match::Bool = true)
```

A|x> と近似 MPS y の距離を計算します: `| |y> - A|x> |/| A|x> | = √(1 + (<y|y> - 2*real(<y|A|x>))/<Ax|A|x>)`。

`make_inds_match = true` の場合、関数は `y` のサイトインデックスを `x` と共通でない `A` のサイトインデックスと一致させようとします。
