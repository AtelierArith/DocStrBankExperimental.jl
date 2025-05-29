```
match_sequentially!(dicts::Vector{Dict{Int, Any}}, matcher::IDMatcher; kw...)
```

`dicts`、すなわちID（整数）を値にマッピングする辞書のベクターを、与えられた`matcher`に従って順次マッチさせるために、最初の要素を除くすべての`dicts`の要素に[`matching_map`](@ref)関数を適用します。

Attractors.jlの文脈において、`dicts`は通常、IDをアトラクタ（`StateSpaceSet`）にマッピングする辞書ですが、この関数は一般的であり、`matcher`が機能する任意の値に対しても動作します。

`rmaps`を返します。`rmaps[i]`には`dicts[i+1]`の[`matching_map`](@ref)が含まれ、すなわち`old => new` IDのペアです。

## キーワード引数

  * `pcurve = nothing`: 継続が行われたパラメータの曲線で、[`matching_map`](@ref)に与えられる`p, pprev`値を抽出するためのものです。これが何を意味するのか不明な場合は、[`global_continuation`](@ref)を参照してください。
  * `ds = nothing`: [`matching_map`](@ref)に伝播されます。
  * `retract_keys::Bool = true`: `true`の場合、関数の最後でキーを「再縮小」します（すなわち、整数を小さい整数にします）ので、すべてのユニークなIDは1増加した正の整数になります。例えば、IDが1、6、8の場合、1、2、3になります。特別なID -1は影響を受けません。
  * `use_vanished = false`: `use_vanished = true`の場合、以前は存在していたが消失したID（およびそれに対応するセット）は、マッチングに関して「メモリ」に保持されます：現在の辞書の値（アトラクタセット）は、これまでに存在したすべての値の最新のインスタンスと比較され、それぞれにユニークなIDが付与され、最も近いものにマッチされます。このキーワードの値は`matcher`から取得されます。
