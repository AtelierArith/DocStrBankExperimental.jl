`DataFrames.jl`で使用するためのペア式を作成する

### 詳細

すべてのシンボルはDataFramesの列を参照するものと仮定されますが、以下の例外があります：

  * `missing`
  * `:call`または`:.`式の最初の`args`（関数呼び出し）
  * スプライシング/補間式`$()`内の引数（プログラム的に列名を参照）
  * `esc()`内の引数（外部変数を参照）

`@rows`も参照してください。

### 例

```julia
julia> using PairsMacros
julia> @cols z = sum(x)
[:x] => sum => :z
julia> u = :y
julia> @cols z = sum($u)
[:y] => sum => :z
julia> @cols $u = sum(x)
[:x] => sum => :y
julia> @cols z = sum($"my variable name")
"my variable name" => sum => :z
julia> @cols z = map(esc(cos), y)
[:y] => (x -> map(cos, x)) => :z
```
