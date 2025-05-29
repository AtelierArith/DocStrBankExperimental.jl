```
check_no_self_qualified_accesses(mod::Module, file=pathof(mod);
                                ignore::Tuple=())
```

`mod` またはそのサブモジュールのいずれも自己修飾アクセスを持たないことを確認し、そうであれば `SelfQualifiedAccessException` をスローし、そうでなければ `nothing` を返します。

これはパッケージのテストで使用できます。例えば、

```julia
@test check_no_self_qualified_accesses(MyPackage) === nothing
```

## 一部の自己修飾アクセスを許可する

`ignore` が指定されている場合、それは自己修飾が許可される名前を表す `Symbol` のタプルであるべきです。例えば、

```julia
@test check_no_self_qualified_accesses(MyPackage; ignore=(:foo,)) === nothing
```

は、名前 `foo` の自己修飾アクセス以外に自己修飾アクセスがないことを確認します。

## 完全に分析できないモジュールは例外を引き起こさない

モジュールが完全に分析できない場合（例えば、動的な `include` 呼び出しがある場合）、分析できなかった非公開名の修飾アクセスは見逃されることに注意してください。[`check_no_stale_explicit_imports`](@ref) や [`check_no_implicit_imports`](@ref) とは異なり、この関数はそのような場合に `UnanalyzableModuleException` をスローしません。

同様の情報にプログラム的にアクセスするための [`improper_qualified_accesses`](@ref) も参照してください。`improper_qualified_accesses` は範囲が広がり、他の種類の不適切なアクセスを報告する可能性がありますが、`check_all_qualified_accesses_are_public` はそうではありません。
