`segment(v::Vector{T}, L::Int; overlap::Union{<:AbstractFloat,Integer}=0, symmetric=false) where {T}`

ベクトル `v` を長さ `L` のセグメントに分割し、`overlap` を L の割合として表現します。`overlap` のデフォルトは `0`（重複なし）です。分割されたセグメントのベクトル $v$ を返します - すなわち `Vector{Vector{T}}` - ここで $\vec{v_i}$ は分割された $i$ 番目のセグメントです。

この関数は常に全体のベクトルをキャプチャしようとし、最終的な分割が長さ L でない場合でもそうします。例えば、

```julia
> x = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
> segment(x, 5)
2-element Vector{Vector{Int64}}:
[1, 2, 3, 4, 5]
[6, 7, 8, 9, 0]

> segment(x, 7)
2-element Vector{Vector{Int64}}:
[1, 2, 3, 4, 5, 6, 7]
[8, 9, 0]
```

`symmetric=true` を設定すると、これが発生した場合、最後の分割が削除されます。

```julia
> segment(x, 3; symmetric=true)
3-element Vector{Vector{Int64}}:
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]
```

`L` がセグメントの長さと等しい場合、`segment` は警告を発し、元のベクトルのみを含むベクトル `[v]` を返します。戻り値は型安全性を保証しますが、ベクトルをその長さを超えて分割することはプログラミングのミスである可能性があるため、警告が発生します。
