```
KernelSizeAligned(Δsize; pad)
KernelSizeAligned(Δs::Integer...;pad)
```

フィルターが位相整列されたままで畳み込み層のカーネルサイズを変更するための戦略。言い換えれば、すべてのフィルターに対して同じ要素インデックスが削除/追加され、'外側'の要素のみが削除または追加されます。

重みを変更するために頂点を入力として呼び出します。

### 例

```jldoctest
julia> using NaiveNASflux, Flux

julia> cv = fluxvertex(Conv((3,3), 1=>1;pad=SamePad()), conv2dinputvertex("in", 1));

julia> cv(ones(Float32, 4,4,1,1)) |> size
(4, 4, 1, 1)

julia> layer(cv).weight |> size
(3, 3, 1, 1)

julia> cv |> KernelSizeAligned(-1, 1; pad=SamePad());

julia> cv(ones(Float32, 4,4,1,1)) |> size
(4, 4, 1, 1)

julia> layer(cv).weight |> size
(2, 4, 1, 1)
```
