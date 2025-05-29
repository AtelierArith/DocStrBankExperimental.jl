```
sparse_triangular_solve(block::Block{LU{F}}, m::CSR{F})
```

Simultaneously solve the block system `X`*`block.blocks` == `B`. `Returns 
