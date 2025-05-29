```
inflate_ir!(ci::CodeInfo, linfo::MethodInstance) -> ir::IRCode
inflate_ir!(ci::CodeInfo, sptypes::Vector{VarState}, argtypes::Vector{Any}) -> ir::IRCode
```

`ci::CodeInfo`-IRを`ir::IRCode`形式に膨張させます。これは、元の`ci::CodeInfo`のフィールドが変更されるインプレース変換であるため、注意して使用する必要があります。
