```
struct BatchedInterface{S <: AbstractVector, I}
function BatchedInterface(indp_syms::Tuple...
```

バッチ呼び出しのための情報を格納する構造体 [`getsym`](@ref) または [`setsym`](@ref)。最初の要素がインデックスプロバイダーで、2番目の要素がインデックスプロバイダー内のシンボリック変数の配列（状態またはパラメータのいずれか）であるタプルを与えると、`BatchedInterface` はすべてのシンボルの和集合を計算し、各シンボルを最初に出現したインデックスプロバイダーに関連付けます。

例えば、2つのインデックスプロバイダー `s1 = SymbolCache([:x, :y, :z])` と `s2 = SymbolCache([:y, :z, :w])` がある場合、`BatchedInterface((s1, [:x, :y]), (s2, [:y, :z]))` は `:x` と `:y` を `s1` に、`:z` を `s2` に関連付けます。`s1` が関連付けたシンボル `:x` と `:y`、および `s2` が関連付けたシンボル `:y` と `:z` の情報も内部的に保持されます。

`BatchedInterface` は、和集合内のシンボルの順序を照会するために [`variable_symbols`](@ref)、[`is_variable`](@ref)、[`variable_index`](@ref) を実装しています。

詳細については [`getsym`](@ref) と [`setsym`](@ref) を参照してください。

また、[`associated_systems`](@ref) も参照してください。
