## DancingLinks

# Exported:

  * exact*cover(matrix::Matrix{Bool}; do*check::Bool) # `matrix` は 'Exact Cover' インシデンス行列です

グローバル変数 `incidence_matrix`, `nrows`, `ncols` を初期化します。これは関数 `solve` が呼び出される前に実行する必要があります。

  * solve(; verbose=false, max_solutions=1, deterministic=false) ::Bool
  * 
  * solve(starting*state::Vector{Int64}; verbose=false, max*solutions=1, deterministic=false) ::Bool

    ```
      starting_state    `提供された制約行列（グローバル変数 `incidence_matrix`）へのインデックスによる行のリストで、
                         削除されるべき行 - それらは解の一部として「与えられた」ものです。`
      [verbose]         `グローバル `VERBOSE` フラグを設定します; タイミングなどを印刷します。`
      [max_solutions]   `グローバル `SOLUTIONSMAX` を設定します; 戻る前に見つけるべき解の数。`
      [deterministic]   `グローバル `DO_DETERMINISTICALLY` を設定します; false=行をランダムに選択します。`
    ```
  * 
  * solutions

見つかった解の結果リスト（各解はグローバル `incidence_matrix` への行インデックスの Vector{Int64} であり、順序付けられています）。

  * 
  * convert_nanoseconds(nanosecs::Real; ncols::Integer=0, units::Union{Nothing, Symbol}=nothing, omitunits::Bool=false)::String
  * 
  * vector*sans*type(vec::AbstractVector)::String

# Example:

```
`# まずインシデンス行列を構築します、Matrix{Bool}`
exact_cover(matrix)
solve() # 'givens' なしでランダムな解を取得します
```

この "DancingLinks" 実装の徹底的なテストについては、パッケージ "Sudoku2" を参照してください。
