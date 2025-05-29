```
randomcircuit(
  coupling_sequence::Vector;
  depth::Int = 1,
  twoqubitgates::Union{String,Vector{String}}="RandomUnitary",
  onequbitgates::Union{Nothing,String,Vector{String}}=nothing,
  layered::Bool=true,
  rng=Random.GLOBAL_RNG)
```

与えられた `depth` で回路を構築します。各層は、`coupling_sequences` のセットに従ってペアの量子ビットに適用される一連の二量子ビットゲートで構成されています。各層には $n$ の単一量子ビットゲートも含まれています。両方のケースで、選択されたゲートはキーワード引数 `onequbitgates` と `twoqubitgates` として渡されます。

デフォルトの構成は、二量子ビットのランダムなハールユニタリと、単一量子ビットゲートはありません。

`layered = true` の場合、返されるオブジェクトは回路層の `Vector` であり、量子ゲートの完全なコレクションではありません。
