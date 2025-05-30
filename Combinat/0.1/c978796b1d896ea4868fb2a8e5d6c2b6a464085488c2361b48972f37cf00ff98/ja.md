`groupby(f::Function,l)`

コレクション `l` の要素を、関数 `f` がそれらに対して取る値に従ってグループ化します。`f` の値はハッシュ可能でなければなりません。

```julia-repl
julia> groupby(iseven,1:10)
Dict{Bool, Vector{Int64}} with 2 entries:
  0 => [1, 3, 5, 7, 9]
  1 => [2, 4, 6, 8, 10]
```

注: 結果のキーは、`l` が空である場合、関数の戻り値の型にアクセスする方法がわからないため、`Any` 型になります。
