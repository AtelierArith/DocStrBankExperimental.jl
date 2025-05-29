```
check_all_explicit_imports_via_owners(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                      require_submodule_import=false,
                                      skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core)),
                                      allow_internal_imports=true)
```

`mod` またはそのサブモジュールが、`Base.which` によって決定された所有者以外のモジュールを介して名前をインポートしていないことを確認します（その名前がそのモジュールで公開されているかエクスポートされている場合を除く）。そうであれば `ExplicitImportsFromNonOwnerException` をスローし、そうでなければ `nothing` を返します。

これはパッケージのテストで使用できます。例えば、

```julia
@test check_all_explicit_imports_via_owners(MyPackage) === nothing
```

## 非所有モジュールからの一部の明示的インポートを許可する

`skip` キーワード引数を渡すことで、いくつかのモジュール（およびそのサブモジュール）からの非所有インポートを許可できます。`importing_from => parent` のペアのタプルを渡すことで、`importing_from` モジュールからインポートされている名前が `parent` モジュールによって所有されている場合を許可します。デフォルトでは、`skip` は `(Base => Core,)` に設定されており、Base からインポートされているが Core に所有されている名前はフラグが立てられません。

例えば：

```julia
@test check_all_explicit_imports_are_public(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

は、DataFrames から PrettyTables に所有されている名前を明示的にインポートすることを許可します。

`ignore` が指定されている場合、それは非所有モジュールからアクセスが許可される名前を表す `Symbol` のタプルである必要があります。例えば、

```julia
@test check_all_explicit_imports_via_owners(MyPackage; ignore=(:DataFrame,)) === nothing
```

は、名前 `DataFrame` 以外の非所有モジュールからの明示的インポートがないことを確認します。

## `require_submodule_import`

`require_submodule_import=true` の場合、所有者モジュールの親モジュールからインポートされていても、非所有モジュールから名前がインポートされている場合はエラーがスローされます。例えば、2024年6月に、`JSON.parse` は実際にはサブモジュール `JSON.Parser` で定義されており、`JSON` 内では公開されていませんが、名前は `JSON` モジュール内に存在します。デフォルトの `require_submodule_import=false` の場合、このシナリオでは `using JSON: parse` へのアクセスはエラーを引き起こしません。`require_submodule_import=false` の場合、エラーを回避するためには `using JSON.Parser: parse` として関数にアクセスする必要があります。

## 完全に分析できないモジュールは例外を引き起こさない

モジュールが完全に分析できない場合（例えば、動的な `include` 呼び出しがある場合）、分析できなかった非公開の名前の明示的インポートは見逃されることに注意してください。[`check_no_stale_explicit_imports`](@ref) や [`check_no_implicit_imports`](@ref) とは異なり、この関数はそのような場合に `UnanalyzableModuleException` をスローしません。

また、プログラム的にそのようなインポートにアクセスするための [`improper_explicit_imports`](@ref) や、より厳密なこのチェックのバージョンである [`check_all_explicit_imports_are_public`](@ref) についても参照してください。`improper_explicit_imports` は範囲が広がり、他の種類の不適切なアクセスを報告する可能性がありますが、`check_all_explicit_imports_via_owners` はそうではありません。
