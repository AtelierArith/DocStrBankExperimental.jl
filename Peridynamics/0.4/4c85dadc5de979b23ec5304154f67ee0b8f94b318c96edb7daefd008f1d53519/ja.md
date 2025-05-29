```
point_set!(body, set_name, points)
point_set!(fun, body, set_name)
```

[`Body`](@ref)にポイントセットを追加します。セットのポイントは、`points::AbstractVector`引数で直接指定するか、フィルタ関数`fun`の結果として指定できます。デフォルトでは、ボディにはすべてのポイントを含む`：all_points`という名前のポイントセットがすでに含まれています。

# 引数

  * `body::AbstractBody`: セットが追加される[`Body`](@ref)。
  * `set_name::Symbol`: ポイントセットの名前。
  * `points::AbstractVector`: セットのポイントインデックスを含むベクトル。インデックスは`body`の`position`および`volume`の範囲内である必要があります。
  * `fun::Function`: ポイントをフィルタリングするための関数。この関数は1つの位置引数のみを受け入れ、`findall`呼び出しで使用されます。引数名に応じて、異なる入力が処理されます：

      * `x`: 関数は`body`の`position`内の各ポイントのx座標を受け取ります：

        ```julia
        points = findall(fun, @view(position[1, :]))
        ```
      * `y`: 関数は`body`の`position`内の各ポイントのy座標を受け取ります：

        ```julia
        points = findall(fun, @view(position[2, :]))
        ```
      * `z`: 関数は`body`の`position`内の各ポイントのz座標を受け取ります：

        ```julia
        points = findall(fun, @view(position[3, :]))
        ```
      * `p`: 関数は`body`の`position`内の各ポイントの各次元を含むベクトルを受け取ります：

        ```julia
        points = findall(fun, eachcol(position))
        ```

# 例外

  * 同じ`set_name`のポイントセットがすでに存在する場合はエラーが発生します。
  * `points`が`body`の`position`および`volume`の範囲外である場合はエラーが発生します。

# 例

x座標がゼロより大きいすべてのポイントを持つポイントセットを`body`に追加します：

```julia-repl
julia> point_set!(x -> x > 0, body, :larger_than_zero)

julia> point_sets(body)
Dict{Symbol, Vector{Int64}} with 2 entries:
  :larger_than_zero => [6, 7, 8, 9, 10, 16, 17, 18, 19, 20  …  9…
  :all_points       => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10  …  991, 9…
```

半径`r`の球の中心の内部に位置するすべてのポイントを持つポイントセットを`body`に追加します。`fun`が`point_set!`の最初の引数であるため、`do`構文を使用できます：

```julia-repl
julia> point_set!(body, :inside_sphere) do p
           sqrt(p[1]^2 + p[2]^2 + p[3]^2) ≤ r
       end

julia> point_sets(body)
Dict{Symbol, Vector{Int64}} with 2 entries:
  :larger_than_zero => [6, 7, 8, 9, 10, 16, 17, 18, 19, 20  …  9…
  :inside_sphere    => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10  …  991, 9…
```
