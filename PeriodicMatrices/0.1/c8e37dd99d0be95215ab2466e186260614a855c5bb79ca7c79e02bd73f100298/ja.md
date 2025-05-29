```
 pgordschur!(S::Vector{Matrix{Float64}}, s::Union{Vector{Bool},BitVector}, Z::Vector{Matrix{Float64}}, select::Union{Vector{Bool},BitVector}; rev, schurindex)
```

固有値の順序を変更します。積 `Π = S[p]^s[p]*...*S[2]^s[2]*S[1]^s[1]` の場合、`rev = true`（デフォルト）であるか、`Π = S[1]^s[1]*S[2]^s[2]*...*S[p]^s[p]` の場合、`rev = false` であるか、`s[j] = ±1` であり、`Π` は実シュール形式で、論理配列 `select` で選択された固有値が先頭に移動されるようにします。 `p`-ベクトル `S` と `Z` は、一般化された周期的シュール形式の行列 `S[1]`, `...`, `S[p]` を含み、`S[schurindex]` は準上三角（実シュール）形式であり、対応する直交変換行列 `Z[1]`, `...`, `Z[p]` をそれぞれ含みます。 `S` と `Z` は更新された行列で上書きされます。 共役の固有値のペアは、`select` を介して両方とも含まれるか、両方とも除外されなければなりません。    
