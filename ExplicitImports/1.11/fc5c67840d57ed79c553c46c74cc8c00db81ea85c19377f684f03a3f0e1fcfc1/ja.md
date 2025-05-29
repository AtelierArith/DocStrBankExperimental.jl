```
improper_explicit_imports(mod::Module, file=pathof(mod); strict=true, skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                          allow_internal_imports=true)
```

`mod`および`mod`のサブモジュール内で発生しているさまざまな種類の「不適切な」明示的インポートを検出しようとします。

現在、2つのクラスの問題を検出します：

  * 明示的にインポートされたが未使用の名前（古い）
  * `mod`内で公開されていない名前

      * ここで、公開とは、エクスポートされているか、`public`キーワードで宣言されていることを意味します（Julia v1.11+が必要）
      * 特にひどい非公開インポートの一例は、名前を「所有」していないモジュールからインポートされる場合です。これに関しては、`importing_from_owns_name`および`importing_from_submodule_owns_name`という返されるフィールドを参照してください。

キーワード引数`allow_internal_imports`は、同じパッケージ内の他のモジュールへの「内部」明示的インポートがここで報告されるかどうかを決定します（または、より一般的には、同じ`Base.moduleroot`を共有する場合）。`allow_internal_imports=false`の場合、そのような「内部」明示的インポートも返されます。

キーワード引数`skip`は、`importing_from => parent`ペアのイテレータであることが期待されており、`importing_from`からインポートされた名前で、`parent`が祖先であるものは無視されます。デフォルトでは、BaseからCoreが所有する名前へのインポートはスキップされます。

この機能はまだ開発中であるため、正確な結果は将来の非破壊的リリースで変更される可能性があります。現在の出力、変更される可能性のあるもの、変更されないもの（ExplicitImports.jlの破壊的リリースなしで）については、引き続きお読みください。

他のモジュールへの不適切な明示的インポートに関する情報を提供するネストされた構造を返します。この情報は、キーが`mod`のサブモジュール（`mod`自体を含む）であるペアのコレクションとして構造化されています。現在、値は`nothing`または以下のキーを持つ`NamedTuple`の`Vector`のいずれかです：

  * `name::Symbol`: インポートされる名前
  * `location::String`: インポートが行われる場所
  * `value::Any`: `mod`内で`name`が指すもの
  * `importing_from::Module`: 名前がインポートされるモジュール（例：`using Foo.X: bar`の場合、これは`X`になります）
  * `whichmodule::Module`: オブジェクトの`Base.which`
  * `public_import::Bool`: `importing_from`内で`name`が公開またはエクスポートされているかどうか。名前が`public`としてマークされているかを確認するには、Julia v1.11+が必要です。
  * `importing_from_owns_name::Bool`: `importing_from`が`whichmodule`と一致するかどうか、したがって名前を直接「所有」していると見なされるかどうか
  * `importing_from_submodule_owns_name::Bool`: `whichmodule`が`importing_from`のサブモジュールであるかどうか
  * `stale::Bool`: 明示的にインポートされた名前が使用されているかどうか
  * `internal_import::Bool`: インポートが「内部」であるかどうか、つまりインポートされたモジュールとインポート元のモジュールが同じ`Base.moduleroot`を共有しているかどうか。

`strict=true`の場合、`mod`が完全に分析できなかった場合は`nothing`を返します。

ExplicitImportsの非破壊的リリースでは：

  * これらの行にさらに列が追加される可能性があります
  * 他の種類の「不適切な」アクセスとして資格を持つ追加の行が返される可能性があります

ただし、結果は少なくとも同じ列を持つTables.jl互換の行指向テーブル（各モジュールごと）になります（または、`strict=true`でモジュールが完全に分析できなかった場合は値が`nothing`になります）。

これらの結果を簡単に計算して印刷するために[`print_explicit_imports`](@ref)を参照してください。また、サブモジュールを無視する非再帰バージョンの[`improper_explicit_imports_nonrecursive`](@ref)、および特定の回帰テストヘルパーの[`check_no_stale_explicit_imports`](@ref)、[`check_all_explicit_imports_via_owners`](@ref)、[`check_all_explicit_imports_are_public`](@ref)も参照してください。
