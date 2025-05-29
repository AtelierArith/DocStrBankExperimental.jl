```
TikzDocument(elements...; use_default_preamble = true, preamble = [])
```

これは通常、`TikzPicture`をラップするLaTeX文書に対応します。

`use_default_preamble`は、グローバル変数から前文が追加されるかどうかを決定します（[`CUSTOM_PREAMBLE`](@ref)および[`CUSTOM_PREAMBLE_PATH`](@ref]を参照）。

`preamble`は、デフォルトのものの後に追加されます（あれば）。

`push!`は、構築後に要素を追加するために使用でき、同様に`push_preamble!`は前文に使用されます。
