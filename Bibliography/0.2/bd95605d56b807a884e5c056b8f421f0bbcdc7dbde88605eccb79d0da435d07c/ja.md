```
sort_bibliography!(
    bibliography::DataStructures.OrderedDict{String,Entry},
    sorting_rule::Symbol = :key
    )
```

文献をその場でソートします。

ソート順は `sorting_rule` を指定することで設定できます。ソートは `isless()` 関数を介して実装されています。詳細については、Julia の `isless()` 実装と `BibInternal.jl` を参照してください。

`soring_rule` にサポートされているシンボルは次のとおりです：

  * `:key` **(デフォルト)**: 文献キー（例：BibTeXキーや `:id`）でソート
  * [`sorting_rules`](@ref) で定義されたソートルール

!!! info "注意:"
    ソートは明示的に文献のアルファベット順の慣習に従っていません。実装された `isless()` 関数（文字列比較器）によって暗黙的に示される標準的な比較器の動作に従っています。

