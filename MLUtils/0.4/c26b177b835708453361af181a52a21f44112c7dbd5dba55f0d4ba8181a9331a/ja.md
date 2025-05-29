```
mapobs(f, data; batched=:auto)
```

データコンテナ `data` の観測値に対して `f` を遅延的に適用します。インデックス指定可能で長さを持つ新しいデータコンテナ `mdata` を返します。インデックス指定は変換 `f` をトリガーします。

キーワード引数 `batched` は `mdata[idx]` および `mdata[idxs]` の動作を制御します。ここで `idx` は整数、`idxs` は整数のベクトルです：

  * `batched=:auto` (デフォルト)。`f` が2つのケースを処理します。 `f(getobs(data, idx))` および `f(getobs(data, idxs))` を呼び出します。
  * `batched=:never`。関数 `f` は常に単一の観測値に対して呼び出されます。 `f(getobs(data, idx))` および `[f(getobs(data, idx)) for idx in idxs]` を呼び出します。
  * `batched=:always`。関数 `f` は常に観測値のバッチに対して呼び出されます。 `getobs(f(getobs(data, [idx])), 1)` および `f(getobs(data, idxs))` を呼び出します。

# 例

```julia
julia> data = (a=[1,2,3], b=[1,2,3]);

julia> mdata = mapobs(data) do x
         (c = x.a .+ x.b,  d = x.a .- x.b)
       end
mapobs(#25, (a = [1, 2, 3], b = [1, 2, 3]); batched=:auto))

julia> mdata[1]
(c = 2, d = 0)

julia> mdata[1:2]
(c = [2, 4], d = [0, 0])
```
