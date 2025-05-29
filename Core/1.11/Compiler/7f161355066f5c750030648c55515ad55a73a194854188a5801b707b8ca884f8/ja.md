```
inflate_ir(ci::CodeInfo, linfo::MethodInstance) -> ir::IRCode
inflate_ir(ci::CodeInfo, sptypes::Vector{VarState}, argtypes::Vector{Any}) -> ir::IRCode
inflate_ir(ci::CodeInfo) -> ir::IRCode
```

非破壊的な `inflate_ir!` のバージョン。主にテストやインタラクティブな使用のために使用されます。
