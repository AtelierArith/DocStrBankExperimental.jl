```
improper_explicit_imports_nonrecursive(mod::Module, file=pathof(mod); strict=true, skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                                       allow_internal_imports=true)
```

[`improper_explicit_imports`](@ref) の非再帰バージョンであり、モジュール `mod` 自体のみを分析し、そのサブモジュールは分析しません。この関数の詳細については、安定性に関する重要な注意事項を含めて、そちらを参照してください（出力は、ExplicitImports! の将来の非破壊的リリースで増加する可能性があります）。

`strict=true` の場合、`mod` を完全に分析できなかった場合は `nothing` を返します。
