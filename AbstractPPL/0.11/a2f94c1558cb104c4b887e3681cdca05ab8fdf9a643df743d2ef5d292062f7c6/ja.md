```
subsumes(u::VarName, v::VarName)
```

変数名 `v` が変数 `u` のサブレンジを記述しているかどうかを確認します。サポートされているインデックス：

  * スカラー：

```jldoctest   julia> subsumes(@varname(x), @varname(x[1, 2]))   true

julia> subsumes(@varname(x[1, 2]), @varname(x[1, 2][3]))   true   ```

  * スカラーの配列：基本的に `issubset` を満たすすべてのもの。

```

jldoctest   julia> subsumes(@varname(x[[1, 2], 3]), @varname(x[1, 3]))   true

julia> subsumes(@varname(x[1:3]), @varname(x[2][1]))   true   ```

  * スライス：

`jldoctest   julia> subsumes(@varname(x[2, :]), @varname(x[2, 10][1]))   true`

現在サポートされていないもの：

  * ブールインデクシング、リテラル `CartesianIndex`（これらは追加可能ですが）
  * 多次元配列の線形インデクシング：行列 `x` に対して `x[4]` は `x[2, 2]` を包含しません
  * トレーリングワン：ベクトル `x` に対して `x[2, 1]` は `x[2]` を包含しません
