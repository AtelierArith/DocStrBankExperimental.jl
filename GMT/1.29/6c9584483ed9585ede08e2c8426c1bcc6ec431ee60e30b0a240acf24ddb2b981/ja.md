```
cv = conv(u::AbstractArray{<:Number, N}, v::AbstractArray{<:Number, N}; shape=:full)
```

二つの配列の畳み込み。

`u,v` がベクトルの場合、ベクトル u と v の畳み込みを返します。`u,v` が行列の場合、行列 A と B の二次元畳み込みを返します。

キーワード引数 `shape` は、完全な畳み込み結果を返すか（デフォルト）、`u` と同じサイズの畳み込みの中央部分のみを返すかを制御します。最初のケース（1Dの場合）では、出力の長さは `length(u) + length(v) - 1` になります。

畳み込みをフィルタリングに使用する場合、通常は `u` と同じサイズの結果を受け取ることに興味があります。この場合、オプション `shape=:same` を使用します（実際、`:full` 以外のものであれば何でも機能します）。しかし、もし多項式を掛け算している場合は、すべての畳み込み項が必要になるため、`shape=:full`（再び、デフォルト）を使用することになります。

### 例

```julia
julia> conv([-1, 2, 3, -2, 0, 1, 2], [2, 4, -1, 1], shape=:same)
7-element Vector{Int64}:
 15
  5
 -9
  7
  6
  7
 -1
```
