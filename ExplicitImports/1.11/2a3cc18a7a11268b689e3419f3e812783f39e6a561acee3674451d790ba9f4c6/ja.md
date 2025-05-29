```
improper_qualified_accesses(mod::Module, file=pathof(mod); skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                            allow_internal_accesses=true)
```

`mod`および`mod`のサブモジュール内で発生するさまざまな種類の「不適切な」修飾アクセスを検出しようとします。

現在のところ、次の条件を満たす場合にのみ、`mod`から名前にアクセスされているケースを検出します：

  * `name`が`mod`からエクスポートされていない
  * または`name`が`mod`で公開されていない（Julia v1.11+が必要）
  * または`name`が「自己修飾」されている：すなわち、モジュール`Foo`内で`Foo.name`にアクセスされている。

キーワード引数`allow_internal_accesses`は、同じパッケージ内の他のモジュールへの「内部」修飾アクセスがここで報告されるかどうかを決定します。`allow_internal_accesses=false`の場合、そのような「内部」修飾アクセスも返されます。自己修飾アクセスは、`allow_internal_accesses`の設定に関係なく報告されます。

キーワード引数`skip`は、`accessing_from => parent`ペアのイテレータであることが期待され、`accessing_from`からアクセスされる名前で、祖先が`parent`であるものは無視されます。デフォルトでは、BaseからCoreが所有する名前へのアクセスはスキップされます。

この機能はまだ開発中であるため、正確な結果は将来の非破壊的リリースで変更される可能性があります。現在の出力、変更される可能性のあるもの、変更されないもの（ExplicitImports.jlの破壊的リリースなしで）については、引き続きお読みください。

他のモジュールへの不適切なアクセスに関する情報を提供するネストされた構造を返します。この情報は、`mod`のサブモジュール（`mod`自体を含む）をキーとするペアのコレクションとして構成されています。現在、値は次のキーを持つ`NamedTuple`の`Vector`です：

  * `name::Symbol`: アクセスされている名前
  * `location::String`: アクセスが行われる場所
  * `value::Any`: `mod`内で`name`が指すもの
  * `accessing_from::Module`: 名前がアクセスされているモジュール（例：`Module.name`）
  * `whichmodule::Module`: オブジェクトの`Base.which`
  * `public_access::Bool`: `accessing_from`内で`name`が公開またはエクスポートされているかどうか。名前が`public`としてマークされているかを確認するには、Julia v1.11+が必要です。
  * `accessing_from_owns_name::Bool`: `accessing_from`が`whichmodule`と一致し、したがって名前を直接「所有」していると見なされるかどうか
  * `accessing_from_submodule_owns_name::Bool`: `whichmodule`が`accessing_from`のサブモジュールであるかどうか
  * `internal_access::Bool`: アクセスが「内部」であるかどうか、つまりアクセスされたモジュールとアクセス元のモジュールが同じ`Base.moduleroot`を共有しているかどうか。
  * `self_qualified::Bool`: アクセスが「自己修飾」であるかどうか、つまりアクセスされたモジュールとアクセス元のモジュールが同じモジュールであるかどうか。

ExplicitImportsの非破壊的リリースでは：

  * これらの行にさらに列が追加される可能性があります
  * 他の種類の「不適切な」アクセスとして資格を持つ追加の行が返される可能性があります

ただし、結果は少なくとも同じ列を持つTables.jl互換の行指向テーブル（各モジュールごと）になります。

これらの結果を簡単に計算して印刷するために[`print_explicit_imports`](@ref)を参照し、サブモジュールを無視する非再帰バージョンの[`improper_qualified_accesses_nonrecursive`](@ref)や、エラーをスローするバージョンの`check_`関数[`check_all_qualified_accesses_via_owners`](@ref)および[`check_all_explicit_imports_are_public`](@ref)を参照してください。回帰テストのために。

## 例

```jldoctest
julia> using ExplicitImports

julia> example_path = pkgdir(ExplicitImports, "examples", "qualified.jl");

julia> print(read(example_path, String))
module MyMod
using LinearAlgebra
# sumは`Base`にあるので、LinearAlgebraからアクセスすべきではありません：
n = LinearAlgebra.sum([1, 2, 3])
end

julia> include(example_path);

julia> row = improper_qualified_accesses(MyMod, example_path)[1][2][1];

julia> (; row.name, row.accessing_from, row.whichmodule)
(name = :sum, accessing_from = LinearAlgebra, whichmodule = Base)
```
