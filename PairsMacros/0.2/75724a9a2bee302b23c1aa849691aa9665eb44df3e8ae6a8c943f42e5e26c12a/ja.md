```markdown
`DataFrames.jl`で使用するためのPairs式を作成します。関数は`ByRow`で囲まれています。

### 詳細

すべてのシンボルはDataFramesの列を参照するものと仮定されていますが、以下の例外があります：

  * `missing`
  * `:call`または`:.`式の最初の`args`（関数呼び出し）
  * スプライシング/補間式`$()`内の引数（プログラム的に列名を参照）
  * `esc`内の引数（外部変数を参照）

`@cols`も参照してください。

### 例

```

julia using PairsMacros julia> @rows z = abs(x) [:x] => ByRow(abs) => :z julia> @rows z = tryparse(esc(Float64), x) [:x] => (x -> tryparse(Float64, x) => :z ```
