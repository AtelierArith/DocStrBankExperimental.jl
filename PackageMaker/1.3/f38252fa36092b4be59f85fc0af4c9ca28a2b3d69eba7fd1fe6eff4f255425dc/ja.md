```
updatecheck_settings(; kwargs...)
```

`PackageMaker`の起動時に更新をチェックするために適用される設定を編集します。

`PackageMaker`は定期的に新しいバージョンが利用可能かどうかを確認します。`updatecheck_settings`関数は、チェックがどのくらいの頻度で行われるかなどを定義する方法の一つです。引数なしで呼び出すと、現在の設定が表示されます。

# kwargs

  * `enabled::Bool`: デフォルトは`true`
  * `default_frequency::Int`: デフォルトでチェックが行われる頻度（日数）。デフォルトは7日です。
  * `next_check::Int`: 今日から次のチェックまでの遅延（日数）。デフォルトは`default_frequency`で、次のチェック後にデフォルトにリセットされます。
  * `skip::Bool`: このバージョンをスキップします。デフォルトは`false`です。

# 例

```julia-repl

julia> PackageMaker.updatecheck_settings(; enabled=false) # もう私を煩わせないで

julia> PackageMaker.updatecheck_settings(; skip=true) # 自分でこのバージョンに更新するかもしれません

julia> PackageMaker.updatecheck_settings(; next_check=365*100) # その時に見てみましょう
```

この関数は公開されていますが、エクスポートされていません。したがって、`PackageMaker.updatecheck_settings(;kwargs...)`として呼び出してください。
