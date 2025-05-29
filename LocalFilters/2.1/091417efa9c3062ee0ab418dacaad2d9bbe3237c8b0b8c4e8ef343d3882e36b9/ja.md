```
localfilter!(dst, A, B, initial, update::Function, final::Function=identity;
             order=FORWARD_FILTER) -> dst
```

は、ソース `A` に対して、`B` によって定義された相対的な近傍に適用されたローカルフィルタの結果で宛先 `dst` を上書きします。`initial`、`update`、および `final` によって実装されます。`initial` 引数は関数である場合とそうでない場合があります。これらの後者の引数の目的は、ローカルフィルタリングを実装する以下の擬似コードによって説明されます。キーワード `order` はフィルタの方向を指定し、デフォルトでは `FORWARD_FILTER` です。

`order = FORWARD_FILTER` の場合：

```
@inbounds for i ∈ indices(dst)
    v = initial isa Function ? initial(A[i]) : initial
    for j ∈ indices(A) ∩ (indices(B) + i)
        v = update(v, A[j], B[j-i])
    end
    dst[i] = final(v)
end
```

`order = REVERSE_FILTER` の場合：

```
@inbounds for i ∈ indices(dst)
    v = initial isa Function ? initial(A[i]) : initial
    for j ∈ indices(A) ∩ (i - indices(B))
        v = update(v, A[j], B[i-j])
    end
    dst[i] = final(v)
end
```

ここで、`indices(A)` は任意の配列 `A` のインデックスの範囲を示し、`indices(B) + i` および `i - indices(B)` はそれぞれ `j` のインデックスの集合を示します。ここで、`j - i ∈ indices(B)` および `i - j ∈ indices(B)` です。言い換えれば、`j ∈ indices(A) ∩ (i - indices(B))` は、すべてのインデックス `j` が `j ∈ indices(A)` かつ `i - j ∈ indices(B)` であることを意味し、したがって `A[j]` と `B[i-j]` は範囲内です。

`initial` が関数である場合、上記の擬似コードにおける状態変数 `v` の初期値は `v = initial(A[i])` で与えられ、`i` は `dst` の現在のインデックスです。したがって、その場合、宛先配列 `dst` とソース配列 `src` は同じ軸を持っている必要があります。

例えば、ローカル最小フィルタ（すなわち、*侵食*）を実装するのは次のように簡単です：

```
localfilter!(dst, A, B, typemax(eltype(A)),
             (v,a,b) -> ifelse(b, min(v,a), v))
```

別の例として、`B` による畳み込みを実装することは次のように書きます：

```
T = promote_type(eltype(A), eltype(B))
localfilter!(dst, A, B, zero(T), (v,a,b) -> v + a*b)
```
