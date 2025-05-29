```
lint(obj::T)
```

`obj`に対して関連するすべてのリンタ関数を呼び出します。より具体的には、メソッドテーブルが`lint(obj::T, ::Val{:linter_id})`メソッド（ここで`:linter_id`は実際のIDの代わりです）を検索し、各特定のリンタ関数が呼び出され、その結果が結合されます。

!!! note
    各特定のリンタ関数は、関連する`LintItem`のベクターを返す必要があります。すなわち、

    ```julia
    lint(obj::T, ::Val{:linter_id}) -> Union{Vector{LintItem{T}}, LintItem{T}, Nothing}
    ```

    `LintItem`の構築方法についての詳細は、ドキュメントを参照してください。

