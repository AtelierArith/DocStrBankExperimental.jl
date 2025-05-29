```
explicit_imports(mod::Module, file=pathof(mod); skip=(mod, Base, Core), strict=true)
```

モジュール `mod` の各サブモジュールに対して行うことができる明示的なインポート文に関する情報を提供するネストされた構造を返します。この情報は、キーが `mod` のサブモジュール（`mod` 自体を含む）であり、値が `NamedTuple` であるペアのコレクションとして構造化されており、どの名前が暗黙的に使用されているか、どのモジュールで定義されているか、どのモジュールからエクスポートされているか、そしてそれらの使用の場所を示しています。将来的には、非破壊的なリリースの中で `NamedTuple` に追加のキーが追加される可能性があります。

## 引数

  * `mod::Module`: （再帰的に）分析するモジュール。通常、これはパッケージです。
  * `file=pathof(mod)`: これはモジュール `mod` を含むソースコードへのパスである必要があります。

      * `mod` がパッケージのトップレベルモジュールである場合、`pathof` はコードを見つけることができず、`mod` を含むファイル（直接または `include` を通じて間接的に）を渡す必要があります。
      * `mod` は `file` 内で定義されたサブモジュールであることができますが、同じ名前のモジュールが2つある場合（例：`X.Y.X` と `X`）、結果が不正確になる可能性があります。

## キーワード引数

  * `skip=(mod, Base, Core)`: リストされたモジュール（またはそのサブモジュール）からの名前はスキップされます。デフォルトで `mod` が含まれているため、`mod` のサブモジュールからエクスポートされた名前の暗黙的なインポートはデフォルトではカウントされません。
  * `strict=true`: `strict` が設定されている場合、分析が正確に実行できなかった場合、モジュールの結果は `nothing` になります。例えば、動的な `include` 文が原因です。`strict=false` の場合、すべてのケースで結果が返されますが、不正確な可能性があります。

!!! note
    `mod` がパッケージである場合、この関数を呼び出す前にそれらの拡張が明示的にロードされていれば、パッケージ拡張内の明示的なインポートを検出できます。

    例えば、`PackageA` がモジュール `PkgBPkgCExt` 内で `PackageB` と `PackageC` に弱い依存関係を持っているとします。

    ```julia-repl
    julia> using ExplicitImports, PackageA

    julia> explicit_imports(PackageA) # PackageA とそのサブモジュール内の明示的なインポートのみをチェックしますが、`PkgBPkgCExt` ではチェックしません
    ```

    `PkgBPkgCExt` 内の明示的なインポートをチェックするには、次のようにします。

    ```julia-repl
    julia> using ExplicitImports, PackageA, PackageB, PackageC

    julia> explicit_imports(PackageA) # これで PackageA とそのサブモジュール、さらに `PkgBPkgCExt` 内の明示的なインポートをチェックします
    ```


[`print_explicit_imports`](@ref) を参照して、これらの結果を簡単に計算して印刷し、サブモジュールを無視する非再帰バージョンの [`explicit_imports_nonrecursive`](@ref) や、回帰テストのためにエラーをスローするバージョンの [`check_no_implicit_imports`](@ref) を参照してください。
