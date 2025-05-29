```
check_all_qualified_accesses_are_public(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                        skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,),
                                        allow_internal_accesses=true)
```

`mod` またはそのサブモジュールが、非公開の名前（すなわち、エクスポートされていない、または Julia 1.11+ で公開と宣言されていない名前）への修飾アクセスを持たないことを確認し、そうであれば `NonPublicQualifiedAccessException` をスローし、そうでなければ `nothing` を返します。

これはパッケージのテストで使用できます。例えば、

```julia
@test check_all_qualified_accesses_are_public(MyPackage) === nothing
```

## 一部の非公開修飾アクセスを許可する

`skip` キーワード引数を渡すことで、いくつかのモジュール（およびそのサブモジュール）からの非公開修飾アクセスを許可できます。`accessing_from => pub` のペアのタプルを渡すことで、`accessing_from` モジュールからアクセスされている名前が、`pub` モジュールで公開されている場合を許可します。デフォルトでは、`skip` は `(Base => Core,)` に設定されており、Base からアクセスされるが Core で公開されている名前はフラグが立てられません。

例えば：

```julia
@test check_all_qualified_accesses_are_public(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

は、DataFrames から PrettyTables で公開されている名前にアクセスすることを許可します。

`ignore` が指定されている場合、それは非公開のモジュールからアクセスが許可される名前を表す `Symbol` のタプルである必要があります。例えば、

```julia
@test check_all_qualified_accesses_are_public(MyPackage; ignore=(:DataFrame,)) === nothing
```

は、名前 `DataFrame` の修飾アクセスを除いて、非公開の修飾アクセスがないことを確認します。

## 完全に分析できないモジュールは例外を引き起こさない

モジュールが完全に分析できない場合（例えば、動的な `include` 呼び出しがある場合）、分析できなかった非公開の名前への修飾アクセスは見逃されることに注意してください。[`check_no_stale_explicit_imports`](@ref) および [`check_no_implicit_imports`](@ref) とは異なり、この関数はそのような場合に `UnanalyzableModuleException` をスローしません。

プログラム的アクセスのための [`improper_qualified_accesses`](@ref) およびキーワード引数 `allow_internal_accesses` の意味、そしてこのチェックの弱いバージョンである [`check_all_qualified_accesses_via_owners`] も参照してください。`improper_qualified_accesses` は範囲が広がり、他の種類の不適切なアクセスを報告する可能性がありますが、`check_all_qualified_accesses_are_public` はそうではありません。
