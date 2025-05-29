```
check_all_qualified_accesses_via_owners(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                        require_submodule_access=false,
                                        skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,
                                                                       Compat => Base,
                                                                       Compat => Core),
                                        allow_internal_accesses=true)
```

`mod` またはそのサブモジュールが、`Base.which` によって決定された所有者以外のモジュールを介して名前にアクセスしていないことを確認します（その名前がそのモジュール内で公開されているかエクスポートされている場合を除く）。そうであれば `QualifiedAccessesFromNonOwnerException` をスローし、そうでなければ `nothing` を返します。

これはパッケージのテストで使用できます。例えば、

```julia
@test check_all_qualified_accesses_via_owners(MyPackage) === nothing
```

## 非所有モジュールを介した一部の資格のあるアクセスを許可する

`skip` キーワード引数を渡すことで、いくつかのモジュール（およびそのサブモジュール）を介した非所有アクセスを許可できます。`accessing_from => parent` のペアのタプルを渡すことで、`accessing_from` モジュールからインポートされている名前が `parent` モジュールによって所有されている場合を許可します。デフォルトでは、`skip` は `(Base => Core,)` に設定されており、Base からアクセスされるが Core に所有される名前はフラグが立てられません。

例えば：

```julia
@test check_all_qualified_accesses_via_owners(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

は、DataFrames から PrettyTables に所有される名前に明示的にアクセスすることを許可します。

`ignore` が指定されている場合、それは非所有モジュールからアクセスが許可される名前を表す `Symbol` のタプルである必要があります。例えば、

```julia
@test check_all_qualified_accesses_via_owners(MyPackage; ignore=(:DataFrame,)) === nothing
```

は、名前 `DataFrame` 以外の非所有モジュールからの資格のあるアクセスがないことを確認します。

`require_submodule_access=true` の場合、所有者モジュールの親モジュールによってアクセスされている場合でも、非所有モジュールによって名前がアクセスされるとエラーがスローされます。例えば、2024年6月に `JSON.parse` は実際にはサブモジュール `JSON.Parser` に定義されており、`JSON` 内では公開されていませんが、その名前はモジュール `JSON` 内に存在します。`require_submodule_access=false`（デフォルト）の場合、このシナリオではアクセス `JSON.parse` はエラーを引き起こしません。なぜなら、その名前は所有者の親によってアクセスされているからです。`require_submodule_access=false` の場合、エラーを避けるためには `JSON.Parser.parse` として関数にアクセスする必要があります。

プログラムによるアクセスのための [`improper_qualified_accesses`](@ref) と、キーワード引数 `allow_internal_accesses` の意味については、また、より厳密なこのチェックのバージョンについては [`check_all_qualified_accesses_are_public`](@ref) を参照してください。`improper_qualified_accesses` は範囲が広がり、他の種類の不適切なアクセスを報告する可能性がありますが、`check_all_qualified_accesses_via_owners` はそうではありません。
