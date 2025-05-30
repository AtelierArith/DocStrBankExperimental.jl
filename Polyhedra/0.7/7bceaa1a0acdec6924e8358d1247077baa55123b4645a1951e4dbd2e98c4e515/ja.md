```
fixandeliminate(p::HRep{T}, I, v)
```

インデックス `I` の変数を対応する値 `v` に固定します。これは次の操作を行うことと同等です：

```julia
function ei(i)
    a = zeros(T, fulldim(p))
    a[i] = one(T)
    a
end
eliminate(p ∩ HyperPlane(ei(I[1]), v[1]) ∩ ... ∩ HyperPlane(ei(I[n]), v[n]))
```

ここで `n` は `I`（および `v`）の長さですが、はるかに効率的です。上記のコードは多面体の射影を行いますが、この関数は各半空間 `⟨a, x⟩ ≤ β`（または各超平面 `⟨a, x⟩ = β`）を半空間 `⟨a_J, x⟩ ≤ β - ⟨a_I, v⟩`（または超平面 `⟨a_J, x⟩ = β - ⟨a_I, v⟩`）に置き換えます。ここで `J = setdiff(1:fulldim(p), I)` です。
