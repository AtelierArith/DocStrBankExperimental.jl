```
position!(P::ProjMPOSum, psi::MPS, pos::Int)
```

MPS `psi` が与えられたとき、ProjMPOSum `P` によって表されるMPOの射影をシフトして、未射影のサイトのセットがサイト `pos` から始まるようにします。この操作は、すでに射影されたサイトのMPOの以前の射影を効率的に再利用します。MPS `psi` は、この操作が成功するために、以前に射影されたMPOテンソルと互換性のあるボンドインデックスを持っている必要があります。
