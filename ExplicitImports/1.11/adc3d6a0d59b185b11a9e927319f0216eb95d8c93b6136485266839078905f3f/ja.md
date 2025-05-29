```
check_all_explicit_imports_are_public(mod::Module, file=pathof(mod); ignore::Tuple=(),
                                      skip::NTuple{N, Pair{Module, Module}} where N=(Base => Core,),
                                      allow_internal_imports=true)
```

`mod` またはそのサブモジュールが非公開の名前（すなわち、エクスポートされていない、または Julia 1.11+ で公開されていると宣言されていない）をインポートしていないことを確認し、そうであれば `NonPublicExplicitImportsException` をスローし、そうでなければ `nothing` を返します。

これはパッケージのテストで使用できます。例えば：

```julia
@test check_all_explicit_imports_are_public(MyPackage) === nothing
```

## 一部の非公開の明示的インポートを許可する

`skip` キーワード引数を渡すことで、特定のモジュール（およびそのサブモジュール）からの非公開インポートを許可できます。`importing_from => pub` のペアのタプルを渡すことで、`importing_from` モジュールからインポートされている名前が `pub` モジュールで公開されている場合を許可します。デフォルトでは、`skip` は `(Base => Core,)` に設定されており、Base からインポートされているが Core で公開されている名前はフラグが立てられません。

例えば：

```julia
@test check_all_explicit_imports_are_public(MyPackage; skip=(Base => Core, DataFrames => PrettyTables)) === nothing
```

は、DataFrames から PrettyTables で公開されている名前を明示的にインポートすることを許可します。

`ignore` が指定されている場合、それは非公開のモジュールからインポートされることが許可されている名前を表す `Symbol` のタプルであるべきです。例えば、

```julia
@test check_all_explicit_imports_are_public(MyPackage; ignore=(:DataFrame,)) === nothing
```

は、名前 `DataFrame` のインポートを除いて、非公開の明示的インポートがないことを確認します。

## 完全に分析できないモジュールは例外を引き起こさない

モジュールが完全に分析できない場合（例えば、動的な `include` 呼び出しがある場合）、分析できなかった非公開の名前の明示的インポートは見逃されます。[`check_no_stale_explicit_imports`](@ref) および [`check_no_implicit_imports`](@ref) とは異なり、この関数はそのような場合に `UnanalyzableModuleException` をスローしません。

また、プログラム的にそのようなインポートにアクセスするための [`improper_explicit_imports`](@ref) と、キーワード引数 `allow_internal_imports` の意味、そしてこのチェックの弱いバージョンである [`check_all_explicit_imports_via_owners`] も参照してください。`improper_explicit_imports` は範囲が広がり、他の種類の不適切なアクセスを報告する可能性がありますが、`check_all_explicit_imports_are_public` はそうではありません。
